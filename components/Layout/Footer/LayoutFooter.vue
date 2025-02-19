<template>
  <footer class="layout-footer">
    <section
      class="layout-footer__primary"
      :class="`layout-footer__primary_theme_${theme}`"
    >
      <div
        :class="oldContainer ? 'layout-footer__primary-container' : 'cds--grid'"
      >
        <div class="cds--row">
          <div class="cds--col-lg-7 cds--col-md">
            <UiLogo
              class="layout-footer__logo"
              :class="`layout-footer__logo_theme_${theme}`"
            />
          </div>
          <LayoutFooterLinksGroup
            v-for="sectionElements in footerElements"
            :key="sectionElements.title"
            class="cds--col-lg-3 cds--col-sm"
            :elements="sectionElements.elements"
            :theme="theme"
            :title="sectionElements.title"
          />
          <LayoutFooterLinksGroup
            class="cds--col-lg-3 cds--col-md layout-footer__stay-connected"
            :elements="stayConnectedElements.elements"
            icons-only
            :theme="theme"
            :title="stayConnectedElements.title"
          />
        </div>
      </div>
    </section>
    <section
      class="layout-footer__secondary"
      :class="`layout-footer__secondary_theme_${theme}`"
    >
      <div
        class="layout-footer__secondary-container"
        :class="{ 'cds--grid': !oldContainer }"
      >
        <div class="caption" :class="`layout-footer__copyright_theme_${theme}`">
          ©Qiskit | All Rights Reserved
        </div>
        <div class="layout-footer__secondary-links">
          <UiLink
            v-for="link in secondaryFooterLinks"
            :key="link.label"
            class="caption layout-footer__secondary-link"
            :class="`layout-footer__secondary-link_theme_${theme}`"
            :url="link.url"
          >
            {{ link.label }}
          </UiLink>
        </div>
      </div>
    </section>
  </footer>
</template>

<script setup lang="ts">
import LogoMedium20 from "@carbon/icons-vue/lib/logo--medium/20";
import LogoSlack20 from "@carbon/icons-vue/lib/logo--slack/20";
import LogoTwitter20 from "@carbon/icons-vue/lib/logo--twitter/20";
import LogoYouTube20 from "@carbon/icons-vue/lib/logo--youtube/20";
import { SocialMedia } from "~/constants/links";
import { IconLink, TextLink } from "~/types/links";

interface Props {
  oldContainer?: boolean;
  theme?: "light" | "dark";
}

interface LinksGroup {
  title: string;
  elements: TextLink[];
}

interface LinksWithIconGroup {
  title: string;
  elements: IconLink[];
}

withDefaults(defineProps<Props>(), {
  oldContainer: false,
  theme: "light",
});

const config = useRuntimeConfig();

const footerElements: LinksGroup[] = [
  {
    title: "Community",
    elements: [
      {
        label: "Events",
        url: "/events",
        segment: {
          cta: "events",
          location: "menu",
        },
      },
      {
        label: "Advocates",
        url: "/advocates#become-an-advocate",
      },
      {
        label: "Code of conduct",
        url: "https://github.com/Qiskit/qiskit/blob/master/CODE_OF_CONDUCT.md",
        segment: {
          cta: "code-of-conduct",
          location: "footer",
        },
      },
    ],
  },
  {
    title: "Support",
    elements: [
      SocialMedia.github,
      SocialMedia.support,
      {
        label: "Documentation",
        url: `${config.public.siteUrl}/documentation/`,
      },
    ],
  },
];

const stayConnectedElements: LinksWithIconGroup = {
  title: "Stay Connected",
  elements: [
    {
      ...SocialMedia.twitter,
      icon: LogoTwitter20,
    },
    {
      ...SocialMedia.slack,
      icon: LogoSlack20,
    },
    {
      ...SocialMedia.youtube,
      icon: LogoYouTube20,
    },
    {
      ...SocialMedia.medium,
      icon: LogoMedium20,
    },
  ],
};

const secondaryFooterLinks: TextLink[] = [
  {
    label: "Terms of use",
    url: "https://www.ibm.com/legal?lnk=flg-tous-usen",
  },
  {
    label: "Accessibility",
    url: "https://www.ibm.com/accessibility/us/en/?lnk=flg-acce-usen",
  },
  {
    label: "Contact",
    url: "mailto:hello@qiskit.org",
  },
  {
    label: "Privacy",
    url: "https://quantum-computing.ibm.com/terms/privacy",
  },
];
</script>

<style lang="scss" scoped>
@use "~/assets/scss/carbon.scss";
@use "~/assets/scss/helpers/index.scss" as qiskit;

.layout-footer {
  &__primary {
    padding: carbon.$spacing-07 0;

    &_theme_light {
      background-color: qiskit.$background-color-lighter;
    }

    &_theme_dark {
      background-color: qiskit.$background-color-darker;
    }
  }

  &__secondary {
    padding: carbon.$spacing-07 0;
    padding-bottom: carbon.$spacing-07 + 2.5rem; // make room for the "cookies preferences" button

    &_theme_light {
      background-color: qiskit.$background-color-white;
    }

    &_theme_dark {
      background-color: qiskit.$background-color-black;
    }
  }

  &__primary-container {
    @include qiskit.contained;
  }

  &__logo {
    height: 32px;

    @include carbon.breakpoint-down(md) {
      margin-bottom: carbon.$spacing-07;
    }

    &_theme_light {
      color: qiskit.$text-color-lighter;
    }

    &_theme_dark {
      color: qiskit.$text-color-white;
    }
  }

  &__secondary-link {
    margin-left: carbon.$spacing-07;
    text-decoration: none;

    @include carbon.breakpoint-down(md) {
      margin-bottom: carbon.$spacing-05;
    }

    &:hover {
      text-decoration: underline;
    }

    &_theme_light {
      color: qiskit.$text-color-lighter;
    }

    &_theme_dark {
      color: qiskit.$text-color-white;
    }
  }

  &__secondary-container {
    display: flex;
    justify-content: space-between;

    &:not(.cds--grid) {
      @include qiskit.contained;
    }
  }

  &__secondary-links {
    display: flex;
    justify-content: space-between;

    @include carbon.breakpoint-down(md) {
      flex-direction: column;
    }
  }

  &__stay-connected {
    @include carbon.breakpoint-down(md) {
      margin-top: carbon.$spacing-07;
    }
  }
}
</style>
