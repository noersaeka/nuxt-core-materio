<script setup>
import Filters from '@/views/mis-analytics/filters/Filters.vue'
import AnalyticsNewsSentiment from '@/views/mis-analytics/news/NewsSentiment.vue'
import AnalyticsNewsByIssue from '@/views/mis-analytics/news/NewsByIssue.vue'
import AnalyticsNewsBySource from '@/views/mis-analytics/news/NewsBySource.vue'
import AnalyticsNewsByTime from '@/views/mis-analytics/news/NewsByTime.vue'

</script>

<template>
    <section>
        <VRow>
            <VCol>
                <Filters />
            </VCol>
        </VRow>
        <VRow class="match-height">
            <VCol cols="12" md="6">
                <AnalyticsNewsByIssue />
            </VCol>
            <VCol cols="12" md="6">
                <AnalyticsNewsSentiment />
            </VCol>
        </VRow>

        <VRow class="match-height">
            <VCol cols="12" md="5">
                <AnalyticsNewsBySource />
            </VCol>
            <VCol cols="12" md="7">
                <AnalyticsNewsByTime />
                <!-- <ApexChartBalance /> -->
            </VCol>
        </VRow>
    </section>
</template>