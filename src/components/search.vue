<template>
    <div class="search_container">
        <div class="search_box">
            <input type="text" class="srhkw" placeholder="输入关键字搜索WIKI">
            <span class="search_btn">搜索</span>
        </div>

    </div>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
.search_container {
  height: 48rpx;
  border: 1px solid #5e5e5e;
  border-radius: 10rpx;
  padding: 20rpx;
  background: #f7f7f7;
  .search_box {
    display: flex;
      font-size: 34rpx;
    .srhkw {
      flex: 1;
      height: 100%;
      height: 34rpx;
    }
    .search_btn {
      padding-left: 28rpx;
      border-left: 1rpx solid #000;
      font-family: "PingFang";
    }
  }
}
</style>
