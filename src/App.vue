<template>
  <div id="app">
    <router-view></router-view>
    <tabbar-page></tabbar-page>
    
  </div>
</template>

<script>

import TabbarPage from '@/components/content/TabbarPage/TabbarPage'


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
