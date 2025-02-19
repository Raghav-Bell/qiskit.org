<template>
  <section class="learn-course-recommended-readings">
    <div class="cds--grid cds--no-gutter">
      <div class="cds--row">
        <div class="cds--col-lg-12">
          <h2>External recommended readings</h2>
          <p v-if="preamble">
            {{ preamble }}
          </p>
          <ol class="learn-course-recommended-readings__list">
            <li v-for="reference in references" :key="reference">
              <span class="learn-course-recommended-readings__reference">
                {{ reference }}
              </span>
            </li>
            <li
              v-for="link in links"
              :key="link.label"
              class="learn-course-recommended-readings__list__item"
            >
              <UiLinkText
                class="learn-course-recommended-readings__link"
                :segment="link.segment"
                :url="link.url"
              >
                <span v-if="link.author">
                  {{ link.author }}
                </span>
                <span
                  :class="
                    link.author
                      ? 'learn-course-recommended-readings__title'
                      : ''
                  "
                >
                  {{ link.label }}
                </span>
              </UiLinkText>
              <span v-if="link.description"> - {{ link.description }}</span>
            </li>
          </ol>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { RecommendedReading } from "~/types/learn";

interface Props {
  links: RecommendedReading[];
  references?: string[];
  preamble?: string;
}

withDefaults(defineProps<Props>(), {
  references: () => [],
  preamble: "",
});
</script>

<style lang="scss" scoped>
@use "~/assets/scss/carbon.scss";

.learn-course-recommended-readings {
  &__list {
    list-style: decimal;
    margin-left: carbon.$spacing-05;

    &__item {
      margin-bottom: carbon.$spacing-02;
    }
  }

  &__link {
    width: fit-content;
  }

  &__title {
    font-style: italic;
    margin-left: carbon.$spacing-01;
  }

  &__reference {
    @include carbon.type-style("code-01");

    margin-bottom: carbon.$spacing-01;
  }
}
</style>
