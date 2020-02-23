<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComps/HomeSwiper'

import { getHomeMultidata } from 'network/home'
export default {
  name: 'Home',
  components: {
    NavBar,
    HomeSwiper
  },
  data () {
    return {
      banners: []
    }
  },
  created () {
    this.getHomeMultidata()
  },
  methods: {
    getHomeMultidata() {
        getHomeMultidata().then(res => {
          // this.result = res;
          this.banners = res.data.banner.list
        })
      },
  }
}
</script>

<style scoped>
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
</style>
