<template>
<div id="home">
   <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
   <home-swiper :banners="banners"></home-swiper>
   <HomeRecommend :recommends="recommends"></HomeRecommend>
   <!-- <swiper>
      <swiper-item v-for="item in banners" :key="item.link">
        <a :href="item.link">
            <img :src="item.image" alt="">
        </a>
      </swiper-item>
   </swiper>   -->
</div>           
</template>

<script>
import NavBar from '@/components/common/navbar/NavBar'
// import {Swiper,SwiperItem} from '@/components/common/swiper'
import {getMultiData} from "@/network/home";
import HomeSwiper from "@/views/home/childComp/HomeSwiper"
import HomeRecommend from '@/views/home/childComp/HomeRecommend'



export default {
    name: 'Home',
    data() {
      return {
        banners: [],
        recommends: []
      }
    },
    components: {
      NavBar,
      HomeSwiper,
      HomeRecommend
      // ,Swiper,
      // SwiperItem
    },
   
    created() {
      this._getMultiData()
    },
    methods: {
      _getMultiData(){
        getMultiData().then(res => {
          console.log(res.data.data.banner.list);
          this.banners = res.data.data.banner.list;
          this.recommends = res.data.data.recommend.list;
        })
      }
    }
}
 
</script>


<style scoped>
  #home {
    height: 100vh;
    position: relative;
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #fff;
    position: relative;
    z-index: 9;
  }

  .tab-control {
    position: relative;
    z-index: 9;
  }

  .content {
    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }
</style>