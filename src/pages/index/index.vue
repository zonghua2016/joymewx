<template>
  <div class="container">
    <image class="logo" src="../../../static/imgs/logo.png" mode="scaleToFill"/>
    <Search/>
    <History />
    <Swiper />
    <Letter />
  </div>
</template>

<script>
import Search from "@/components/search.vue";
import History from '@/components/history.vue';
import Swiper from '@/components/swiper.vue';
import Letter from '@/components/letter.vue';
export default {
  data() {
    return {};
  },
  components: {
    Search,
    History,
    Swiper,
    Letter
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
