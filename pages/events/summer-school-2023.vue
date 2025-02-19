<template>
  <article class="summer-school-2023-page">
    <LayoutLeadSpaceWithCard :card-title="headerData.cardSectionHeading">
      <template #title>
        {{ headerData.titleLine1 }}
        <br />
        {{ headerData.titleLine2 }}
      </template>
      <template #description>
        <p>
          The Qiskit Global Summer School 2023 is a two-week intensive summer
          program designed to empower the quantum researchers and developers of
          tomorrow with the know-how to explore the world of quantum computing,
          as well as refresh and sharpen the industry professional's skills.
          This fourth-annual summer school will focus foundationally on quantum
          computing by taking a <b>back-to-basics</b> approach, with a look at
          making the <b>transition</b> from <b>theory to implementation</b>.
        </p>
        <p>
          Please follow
          <UiLinkText :link="headerData.qiskitTwitterLink"
            >Qiskit Twitter</UiLinkText
          >
          for updates and
          <UiLinkText :link="headerData.researchBlogLink">
            read the announcement blog
          </UiLinkText>
          for more details. For any questions, please check out our FAQ below!
        </p>
        <p>See you next year!</p>
      </template>
      <template #card>
        <EventsCard
          :alt-text="header.card.altText"
          class="summer-school-2023-page__header-card"
          :cta-label="headerData.card.ctaLabel"
          :date="headerData.card.date"
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

    <div class="cds--grid summer-school-2023-page__content">
      <UiMosaicSection
        class="summer-school-2023-page__section"
        :title="mosaicData.title"
        :elements="mosaicData.tiles"
      />

      <section class="summer-school-2023-page__section">
        <h2 v-text="agendaData.title" />
        <p v-text="agendaData.subtitle" />
        <bx-tabs trigger-content="Select an item" value="Week 1">
          <bx-tab
            v-for="week in agendaData.weeks"
            :key="week.tabName"
            :target="week.tabName"
            :value="week.tabName"
          >
            {{ week.tabName }}
          </bx-tab>
        </bx-tabs>
        <div class="summer-school-2023-page__agenda">
          <div
            v-for="week in agendaData.weeks"
            :id="week.tabName"
            :key="week.tabName"
            class="summer-school-2023-page__agenda__table"
            role="tabpanel"
            :aria-labelledby="week.tabName"
            hidden
          >
            <UiDataTable :columns="agendaColumnsDataTable">
              <bx-table-row
                v-for="(row, rowIndex) in week.tableData"
                :key="`${rowIndex}`"
              >
                <bx-table-cell
                  v-for="({ styles, data }, elementIndex) in row"
                  :key="`${elementIndex}`"
                >
                  <span :style="styles">{{ data }}</span>
                </bx-table-cell>
              </bx-table-row>
            </UiDataTable>
          </div>
        </div>
      </section>

      <EventsSummerSchoolFaq2023 class="summer-school-2023-page__section" />

      <UiHelpfulResources
        class="summer-school-2023-page__section"
        :title="helpfulResourcesData.title"
        :resources="helpfulResourcesData.resources"
      />
    </div>
  </article>
</template>

<script setup lang="ts">
import {
  header,
  mosaic,
  agenda,
  helpfulResources,
} from "~/constants/summerSchool2023Content";

definePageMeta({
  pageTitle: "Qiskit Global Summer School 2023",
  routeName: "/events/summer-school-2023",
});

const config = useRuntimeConfig();

const title = "Qiskit Global Summer School 2023";
const description =
  "Empowering the next generation of quantum researchers at the Qiskit Global Summer School 2023, a two-week intensive program focusing on quantum applications.";
const image = `${config.public.siteUrl}/images/events/summer-school-2023/summer-school-2023-logo.png`;
const pageUrl = `${config.public.siteUrl}/events/summer-school-2023`;

useSeoMeta({
  title,
  ogTitle: title,
  description,
  ogDescription: description,
  ogImage: image,
  ogImageAlt: title,
  ogUrl: pageUrl,
});

const agendaColumnsDataTable: string[] = ["Day", "Topic", "Speaker", "Format"];
const headerData = header;
const mosaicData = mosaic;
const agendaData = agenda;
const helpfulResourcesData = helpfulResources;

useSchemaOrg([
  createEventSchemaOrg({
    startDate: new Date("2023-07-17"),
    mode: "Online",
    location: "",
    url: `${config.public.siteUrl}/events/summer-school-2023/`,
    name: headerData.card.title,
    image: `${config.public.siteUrl}${headerData.card.image}`,
    endDate: new Date("2023-07-28"),
  }),
]);
</script>

<style lang="scss" scoped>
@use "~/assets/scss/carbon.scss";
@use "~/assets/scss/helpers/index.scss" as qiskit;

.summer-school-2023-page {
  display: flex;
  flex-direction: column;

  &__section {
    margin-top: carbon.$spacing-10;
    margin-bottom: carbon.$spacing-07;

    @include carbon.breakpoint-down(lg) {
      margin-bottom: carbon.$spacing-05;
    }
  }

  &__agenda {
    margin-top: carbon.$spacing-07;
    margin-bottom: carbon.$spacing-07;

    @include carbon.breakpoint-down(lg) {
      margin-bottom: carbon.$spacing-05;
    }

    &__table {
      max-width: 100%;
      overflow-x: scroll;
    }
  }

  &__content {
    @include carbon.breakpoint-down(lg) {
      max-width: 100%;
    }
  }

  &__header-card {
    :deep(.card__image-container) {
      flex: 0 0 24rem;
    }
  }
}
</style>
