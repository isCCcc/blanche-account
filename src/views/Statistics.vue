<template>
  <Layout>
    <Tabs :data-source="recordTypeList" :value.sync="type"></Tabs>
    <StatisticsContent :type="type"></StatisticsContent>
  </Layout>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component} from 'vue-property-decorator';
import Tabs from '@/components/Money/Tabs.vue';
import recordTypeList from '@/constant/recordTypeList';
import StatisticsContent from '@/components/Statistics/StatisticsContent.vue';

@Component({
  components: {StatisticsContent, Tabs}
})
export default class Statistics extends Vue {
  recordTypeList = recordTypeList;
  type = '-';


}
</script>
