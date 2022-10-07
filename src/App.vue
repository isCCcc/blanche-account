<template>
  <div id="app">
    <!--    <router-view v-slot="{Component}">-->
    <!--      <transition name="fade" mode="out-in">-->
    <!--        <component :is="Component"/>-->
    <!--      </transition>-->
    <!--    </router-view>-->
    <transition name="fade" mode="out-in">
      <router-view/>
    </transition>
  </div>
</template>

<style lang="scss">
@import "~@/assets/style/reset.scss";
@import "~@/assets/style/helper.scss";

body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-family: $font-hei;
  color: #333;
  line-height: 1.5;
  font-size: 16px;

}

#app {
  overflow-x: hidden;
  margin: 0;

  .fade-enter-active,
  .fade-leave-active {
    transition: all 100ms ease;
  }

  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }

  .fade-enter-to,
  .fade-leave-from{
    opacity: 1;
  }

}
</style>
