<template>
  <article class="fall-fest-page">
    <LayoutLeadSpaceWithCard
      :cta="headerData.cta"
      :card-title="headerData.cardSectionHeading"
    >
      <template #title>
        {{ headerData.titleLine1 }}
      </template>
      <template #description>
        <p>
          The Qiskit Fall Fest is a collection of quantum computing events on
          college campuses around the world. Every Fall Fest event is organized
          and run by the students on each campus, with support from the entire
          IBM Quantum team. Student leaders work alongside IBM throughout the
          month of September to design and plan their event, which are then run
          in October. The events vary from technical hackathons to
          beginner-friendly challenges, all with the goal of helping to grow the
          local community’s skill set.
        </p>
      </template>
      <template #card>
        <EventsCard
          :cta-label="headerData.card.ctaLabel"
          :image="headerData.card.image"
          :location="headerData.card.location"
          :segment="headerData.card.segment"
          :time="headerData.card.time"
          :title="headerData.card.title"
          :to="headerData.card.to"
          vertical-layout
        >
          {{ headerData.card.description }}
        </EventsCard>
      </template>
    </LayoutLeadSpaceWithCard>

    <div class="cds--grid fall-fest-page__content">
      <section class="fall-fest-page__section">
        <EventsFallFestUniversityDirectory />
      </section>
    </div>

    <div class="cds--grid fall-fest-page__content">
      <section class="fall-fest-page__section">
        <h2 v-text="agendaData.title" />
        <p v-text="agendaData.subtitle" />
        <bx-tabs value="Wave 1">
          <bx-tab
            v-for="week in agendaData.weeks"
            :key="week.tabName"
            :target="week.tabName"
            :value="week.tabName"
          >
            {{ week.tabName }}
          </bx-tab>
        </bx-tabs>
        <div
          v-for="week in agendaData.weeks"
          :id="week.tabName"
          :key="week.tabName"
          :aria-labelledby="week.tabName"
          role="tabpanel"
          hidden
        >
          <UiDataTable
            class="fall-fest-page__section"
            :columns="agendaColumnsDataTable"
          >
            <bx-table-row
              v-for="(row, rowIndex) in week.tableData"
              :key="`${rowIndex}`"
            >
              <bx-table-cell
                v-for="({ styles, data, link }, elementIndex) in row"
                :key="`${elementIndex}`"
              >
                <UiLinkText
                  v-if="link"
                  class="fall-fest-page__table-link"
                  :style="styles"
                  :url="link"
                >
                  Link to event
                </UiLinkText>
                <span v-else :style="styles">{{ data }}</span>
              </bx-table-cell>
            </bx-table-row>
          </UiDataTable>
        </div>
      </section>

      <UiHelpfulResources
        class="fall-fest-page__section"
        :title="helpfulResourcesData.title"
        :resources="helpfulResourcesData.resources"
      />
    </div>
  </article>
</template>

<script setup lang="ts">
import {
  header,
  agenda,
  helpfulResources,
} from "~/constants/fallFest2022Content";

definePageMeta({
  pageTitle: "Qiskit Fall Fest 2022",
  routeName: "fall-fest",
});

const config = useRuntimeConfig();

const title = "Qiskit Fall Fest 2022";
const description =
  "The Qiskit Fall Fest is a collection of quantum computing events from universities around the world, organized by students and supported by the IBM Quantum community.";
const image = `${config.public.siteUrl}/images/events/fall-fest/fall-fest.png`;
const pageUrl = `${config.public.siteUrl}/events/summer-school-2023`;

useSeoMeta({
  title,
  ogTitle: title,
  description,
  ogDescription: description,
  ogImage: image,
  ogImageAlt: title,
  ogUrl: pageUrl,
  ogType: "website",
  twitterCard: "summary_large_image",
  twitterDescription: description,
});

const agendaData = agenda;
const agendaColumnsDataTable: string[] = [
  "University",
  "Start Date",
  "End Date",
  "Detail",
  "Type of Event",
  "Link",
];
const headerData = header;
const helpfulResourcesData = helpfulResources;
</script>

<style lang="scss" scoped>
@use "~/assets/scss/carbon.scss";
@use "~/assets/scss/helpers/index.scss" as qiskit;

.fall-fest-page {
  display: flex;
  flex-direction: column;

  &__section {
    margin-top: carbon.$spacing-10;
    margin-bottom: carbon.$spacing-07;

    @include carbon.breakpoint-down(lg) {
      margin-bottom: carbon.$spacing-05;
    }
  }

  &__content {
    @include carbon.breakpoint-down(lg) {
      max-width: 100%;
    }
  }
}
</style>
