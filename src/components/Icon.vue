<template>
  <svg class="icon">
    <use :xlink:href="'#'+name" />
  </svg>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

// 导入icons目录
// eslint-disable-next-line no-undef
const importAll = (requireContext: __WebpackModuleApi.RequireContext) => requireContext.keys().forEach(requireContext);
try {importAll(require.context('../assets/icons', true, /\.svg$/));} catch (error) {console.log(error);}

@Component
export default class Icon extends Vue {
  @Prop(String) name!:string;
}
</script>

<style lang="scss" scoped>
.icon{
  width: 1em;
  height: 1em;
  font-family:"iconfont" !important;
  font-size:56px;
  font-style:normal;
  -webkit-font-smoothing: antialiased;
  -webkit-text-stroke-width: 0.2px;
  -moz-osx-font-smoothing: grayscale;
}
</style>