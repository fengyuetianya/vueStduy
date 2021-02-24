<template>
  <div id="app">
    <tabbar-page></tabbar-page>
    <router-view></router-view>
  </div>
</template>

<script>

import TabbarPage from '@/components/content/TabbarPage'


export default {
  name: 'App',
  components: {
    TabbarPage

  }
  
}
</script>

<style>
  @import "assets/css/base.css";
</style>
