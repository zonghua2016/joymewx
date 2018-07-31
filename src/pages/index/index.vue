<template>
  <div class="container">
    <image class="logo" src="../../../static/imgs/logo.png" mode="scaleToFill"/>
    <Search :keyword="keyword"/>
    <History @getHiskw="getHiskw" />
    <Swiper />
  </div>
</template>

<script>
import Search from "@/components/search.vue";
import History from '@/components/history.vue';
import Swiper from '@/components/swiper.vue';
export default {
  data() {
    return {
      keyword: ''
    };
  },
  methods: {
    getHiskw(kw) {
      console.log(kw);
      this.keyword = kw;
    }
  },
  components: {
    Search,
    History,
    Swiper
  }
};
</script>

<style lang="scss" scoped>
@import "../../common/styles/layout.scss";
.container {
  position: relative;
  padding: 0;
  .logo {
    display: block;
    width: 280rpx;
    height: 54rpx;
    margin: 20rpx auto;
  }
}
</style>
