<script setup>
const borderColor = 'rgba(var(--v-border-color), var(--v-border-opacity))'

// Topics Charts config
const topicsChartConfig = {
  chart: {
    height: 270,
    type: 'bar',
    toolbar: { show: false },
  },
  plotOptions: {
    bar: {
      horizontal: true,
      barHeight: '70%',
      distributed: true,
      borderRadius: 7,
      borderRadiusApplication: 'end',
    },
  },
  colors: [
    'rgba(var(--v-theme-primary),1)',
    '#16B1FF',
    '#56CA00',
  ],
  grid: {
    borderColor,
    strokeDashArray: 10,
    xaxis: { lines: { show: true } },
    yaxis: { lines: { show: false } },
    padding: {
      top: -35,
      bottom: -12,
    },
  },
  dataLabels: {
    enabled: true,
    style: {
      colors: ['#fff'],
      fontWeight: 200,
      fontSize: '13px',
    },
    offsetX: 0,
    dropShadow: { enabled: false },
    formatter(val, opt) {
      return topicsChartConfig.labels[opt.dataPointIndex]
    },
  },
  labels: [
    'Banten Kesehatan',
    'Banten Pembangunan',
    'Banten Korupsi',
  ],
  xaxis: {
    categories: [
      '3',
      '2',
      '1',
    ],
    axisBorder: { show: false },
    axisTicks: { show: false },
    labels: {
      style: {
        colors: 'rgba(var(--v-theme-on-background), var(--v-disabled-opacity))',
        fontSize: '13px',
      },
      formatter(val) {
        return `${val}%`
      },
    },
  },
  yaxis: {
    max: 35,
    labels: {
      style: {
        colors: 'rgba(var(--v-theme-on-background), var(--v-disabled-opacity))',
        fontSize: '13px',
      },
    },
  },
  tooltip: {
    enabled: true,
    style: { fontSize: '12px' },
    onDatasetHover: { highlightDataSeries: false },
  },
  legend: { show: false },
}

const topicsChartSeries = [{
  data: [
    35,
    27,
    29,
  ],
}]

const topicsData = [
  {
    title: 'Banten Kesehatan',
    value: 35,
    color: 'primary',
  },
  {
    title: 'Banten Pembangunan',
    value: 27,
    color: 'info',
  },
  {
    title: 'Banten Korupsi',
    value: 29,
    color: 'success',
  },
]

const moreTopics = [
  {
    title: 'Animation',
    value: 12,
    color: 'secondary',
  },
  {
    title: 'Vue',
    value: 10,
    color: 'error',
  },
  {
    title: 'SEO',
    value: 9,
    color: 'warning',
  },
]
</script>

<template>
  <VCard>
    <VCardItem title="News By Issue (Keyword)">
      <template #append>
        <div class="me-n3">
          <MoreBtn />
        </div>
      </template>
    </VCardItem>

    <VCardText>
      <VRow>
        <VCol cols="12" sm="6">
          <VueApexCharts type="bar" height="300" :options="topicsChartConfig" :series="topicsChartSeries"
            class="mb-md-0 mb-6" />
        </VCol>

        <VCol class="d-flex justify-space-around align-center">
          <div class="d-flex flex-column gap-y-12">
            <div v-for="topic in topicsData" :key="topic.title" class="d-flex gap-x-2">
              <VBadge inline dot :color="topic.color" class="mt-1" />
              <div>
                <div class="text-body-1" style="min-inline-size: 90px;">
                  {{ topic.title }}
                </div>
                <h5 class="text-h5">
                  {{ topic.value }}%
                </h5>
              </div>
            </div>
          </div>
          <!-- 
          <div class="d-flex flex-column gap-y-12">
            <div v-for="topic in moreTopics" :key="topic.title" class="d-flex gap-x-2">
              <VBadge inline dot :color="topic.color" class="mt-1" />
              <div>
                <div class="text-body-1" style="min-inline-size: 90px;">
                  {{ topic.title }}
                </div>
                <h5 class="text-h5">
                  {{ topic.value }}%
                </h5>
              </div>
            </div>
          </div> -->
        </VCol>
      </VRow>
    </VCardText>
  </VCard>
</template>

<style lang="scss" scoped>
@use "@core/scss/template/libs/apex-chart.scss";

.topicCard {
  .v-badge.v-badge--dot {
    .v-badge__badge {
      border-radius: 6px;
      block-size: 12px;
      inline-size: 12px;
    }
  }
}
</style>
