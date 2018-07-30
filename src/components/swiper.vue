<template>
    <div class="swiper_container">
        <div class="swiper_group">
            <scroll-view class="swiper_items" scroll-x="true" scroll-with-animation="true">
                <span class="sel"><i>全部</i></span>
                <span><i>热门游戏</i></span>
                <span><i>日系游戏</i></span>
                <span><i>女性向游戏</i></span>
                <span><i>无线游戏</i></span>
                <span><i>武侠游戏</i></span>
                <span><i>热门游戏</i></span>
                <span><i>热门游戏</i></span>
                <span><i>热门游戏</i></span>
                <span><i>热门游戏</i></span>
            </scroll-view>
        </div>
        <div class="game_group">
            <div class="tit">ABC</div>
            <div class="game_items">
                <div class="game" v-for="(item,index) in games" :key="index">
                    <img v-lazy="item.imgsrc">
                    <h2 class="game_name">{{item.name}}</h2>
                </div>
            </div>
        </div> 
    </div>
</template>
<script>
export default {
    data(){
        return{
            games:[
                {
                    name: 'dsdfsdfs',
                    imgsrc: 'http://p2.qhimgs4.com/t01b0a970f646f800d2.webp'
                }
            ]
        }
    }
};
</script>
<style lang="scss" scoped>
.swiper_container {
  .swiper_group {
    position: relative;
    width: 100%;
    overflow: hidden;
    &:after {
      display: inline-block;
      position: absolute;
      content: "";
      right: 0;
      top: 0;
      width: 60rpx;
      height: 100%;
      background: rgba(255, 255, 255, 0.8);
    }
    .swiper_items {
      display: flex;
      white-space: nowrap;
      padding: 0 30rpx 0 12rpx;
      border: 1rpx solid #ddd;
      border-left: none;
      border-right: none;
      background: #fff;
      span {
        display: inline-block;
        padding: 0 18rpx;
        &.sel {
          i {
            position: relative;
            color: #000;
            //   font-weight: bold;
            &::after {
              display: inline-block;
              position: absolute;
              content: "";
              background: #42baa1;
              width: 100%;
              height: 4rpx;
              bottom: 0rpx;
              left: 0;
            }
          }
        }
        i {
          font-size: 30rpx;
          line-height: 100rpx;
          color: #999;
        }
      }
    }
  }
  .game_group {
    .tit {
      padding-left: 30rpx;
      font-size: 20rpx;
      line-height: 50rpx;
      background: #f0f0f0;
    }
    .game_items {
      display: flex;
      flex-flow: row wrap;
      padding: 30rpx 25rpx 0 5rpx;
      .game {
        margin: 0 25rpx 30rpx;
        img {
          width: 128rpx;
          height: 128rpx;
          border-radius: 24rpx;
          margin-bottom: 20rpx;
        }
        .game_name {
          font-size: 26rpx;
          text-align: center;
        }
      }
    }
  }
}
</style>
