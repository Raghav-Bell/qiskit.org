<template>
  <UiCard
    class="events-card"
    :image="image"
    :title="title"
    :primary-tags="regions"
    :secondary-tags="types"
    :to="to"
    :cta-label="ctaLabel"
    :segment="segment"
    :vertical-layout="verticalLayout"
    :alt-text="altText"
  >
    <div class="events-card__description">
      <slot v-if="$slots.default" />
    </div>
    <div>
      <div v-if="location" class="events-card__detail">
        <Map20 class="events-card__icon" />
        {{ location }}
      </div>
      <div v-if="date" class="events-card__detail">
        <Calendar20 class="events-card__icon" />
        <time>{{ date }}</time>
      </div>
      <div v-if="time" class="events-card__detail">
        <Time20 class="events-card__icon" />
        <time>{{ time }}</time>
      </div>
      <div v-if="institution" class="events-card__detail">
        <Education20 class="events-card__icon" />
        {{ institution }}
      </div>
    </div>
  </UiCard>
</template>

<script setup lang="ts">
import Calendar20 from "@carbon/icons-vue/lib/calendar/20";
import Education20 from "@carbon/icons-vue/lib/education/20";
import Map20 from "@carbon/icons-vue/lib/map/20";
import Time20 from "@carbon/icons-vue/lib/time/20";
import { CtaClickedEventProp } from "~/types/segment";

interface Props {
  types?: string[];
  title: string;
  image: string;
  altText?: string;
  institution?: string;
  location?: string;
  date?: string;
  time?: string | null;
  to: string;
  ctaLabel?: string;
  segment?: CtaClickedEventProp | undefined;
  verticalLayout?: boolean;
  regions?: string[];
}

withDefaults(defineProps<Props>(), {
  types: () => [],
  altText: "Event image",
  institution: "",
  ctaLabel: "Join the event",
  date: undefined,
  location: undefined,
  segment: undefined,
  time: undefined,
  verticalLayout: false,
  regions: () => [],
});
</script>

<style lang="scss" scoped>
@use "~/assets/scss/carbon.scss";

.events-card {
  &__description {
    margin-bottom: carbon.$spacing-06;
  }

  &__detail {
    display: flex;
    align-items: center;
    margin-bottom: carbon.$spacing-03;

    &:last-child {
      margin-bottom: initial;
    }
  }

  &__icon {
    margin-right: carbon.$spacing-03;
    fill: currentcolor;
  }
}
</style>
