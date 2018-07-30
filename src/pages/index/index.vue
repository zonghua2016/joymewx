<template>
  <div class="container">
    <image class="logo" src="../../../static/imgs/logo.png" mode="scaleToFill"/>
    <Search/>
    <History />
  </div>
</template>

<script>
import Search from "@/components/search.vue";
import History from '@/components/history.vue';
export default {
  data() {
    return {};
  },
  components: {
    Search,
    History
  }
};
</script>

<style lang="scss" scoped>
@import "../../common/styles/layout.scss";
.container {
  padding: 0 30rpx;
  .logo {
    display: block;
    width: 280rpx;
    height: 54rpx;
    margin: 20rpx auto;
  }
}
</style>
