<template>
  <div class="container">
    <img class="logo" src="../../../static/imgs/logo.png" alt="着迷说">
    <Search/>
  </div>
</template>

<script>
import Search from "@/components/search.vue";
export default {
  data() {
    return {};
  },
  components: {
    Search
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
