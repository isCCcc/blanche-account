<template>
  <div class="tags">
    <div class="new">
      <button @click="createTag">新增标签</button>
    </div>
    <ul class="current">
      <li v-for="tag in tagList" :key="tag"
          :class="{selected:selectedTags.indexOf(tag)>=0}"
          @click="toggle(tag)">{{ tag }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';

@Component
export default class Tags extends Vue {
  tagList = this.$store.state.tagList;
  selectedTags = '';

  // 点击标签
  toggle(tag: string) {
    if(this.selectedTags===tag){
      this.selectedTags=''
    }else{
      this.selectedTags=tag
    }
    this.$emit('update:tags', this.selectedTags);
  }

  // 新增标签
  createTag() {
    const name = window.prompt('请输入标签名称');
    if (name === '')
      window.alert('标签名不可为空');
    else
      this.$store.commit('insertTag', name);
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/helper.scss";

.tags {
  font-size: 14px;
  padding: 16px;
  display: flex;
  flex-grow: 1;
  flex-direction: column-reverse;

  .current {
    display: flex;
    flex-wrap: wrap;

    > li {
      color: $color-dark-gray;
      background: $color-tint-gray;
      $h: 24px;
      height: $h;
      line-height: $h;
      border-radius: $h/2;
      padding: 0 16px;
      margin-right: 12px;
      margin-top: 12px;

      &.selected {
        background: $color-tint-green;
        color: $color-dark-green;
      }
    }
  }

  .new {
    padding-top: 16px;

    button {
      background: transparent;
      border: none;
      color: #999;
      border-bottom: 1px solid;
      padding: 0 4px;
    }
  }
}

</style>