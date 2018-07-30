<template>
    <div class="his_container">
        <div class="title">
            <i></i>
            <span>最近查看记录</span>
        </div>
        <ul class="his_list">
            <li v-for="(item, index) in hisList" :key="index" :ref="item" @click="_getHiskw(item)">{{item}}</li>
        </ul>
    </div>
</template>
<script>
export default {
    data() {
        return{
            hisList: ['最终王冠', '牧羊人 之心', '火焰纹章：英雄', '牧羊人 之心', '火焰纹章：英雄', '牧羊人 之心', '火焰纹章：英雄']
        }
    },
    methods: {
        _getHiskw(item){
            console.log(item);
        }
    }
};
</script>
<style lang="scss" scoped>
.his_container {
  padding-right: 20rpx;
  padding-bottom: 12rpx;
  margin: 0 30rpx;
  .title{
      font-size: 26rpx;
      color: #555;
      margin: 30rpx 0;
      i{
          display: inline-block;
          width: 26rpx; height: 26rpx;
          background: url(../../static/imgs/time.png) no-repeat;
          background-size: cover;
          margin-right: 6rpx;
          margin-top: -5rpx;
          vertical-align: middle;
      }
  }
  .his_list{
      li{
          display: inline-block;
          margin: 0 18rpx 18rpx 0;
          padding: 12rpx 20rpx 15rpx;
          border: 1rpx solid #ddd;
          border-radius: 10rpx;
          font-size: 26rpx;
          color: #000;
      }
  }
}
</style>
