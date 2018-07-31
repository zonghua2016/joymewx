<template>
    <div class="swiper_container">
        <div class="swiper_group">
            <scroll-view class="swiper_items" scroll-x="true" scroll-with-animation="true">
                <span :class="curIndex==index?'sel':''" v-for="(item, index) in game" :key="index" @click="getGameInfo(index)" :ref="index"><i>{{item}}</i></span>
            </scroll-view>
        </div>
        <!-- <div class="tit letTit" v-text="toView"></div> -->
        <scroll-view class="game_groups"
                     scroll-y="true" 
                     scroll-with-animation="true" 
                     @scroll="scroll"
                     :scroll-into-view="toView"
                     style="height: 800rpx;">
            <div class="game_group" ref="gameGroup" id="ABC">
              <div class="tit">ABC</div>
              <div class="game_items">
                  <div class="game" v-for="(item,index) in games" :key="index">
                      <image class="game_icon" lazy-load="true" :src="item.imgsrc" />
                      <h2 class="game_name">{{item.name}}</h2>
                  </div>
              </div>
            </div> 
            <div class="game_group" ref="gameGroup" id="DEF">
              <div class="tit">DEF</div>
              <div class="game_items">
                  <div class="game" v-for="(item,index) in gamedef" :key="index">
                      <image class="game_icon" lazy-load="true" :src="item.imgsrc" />
                      <h2 class="game_name">{{item.name}}</h2>
                  </div>
              </div>
            </div> 
        </scroll-view>
        <!-- <div class="game_groups">
            <scroll class="game_group"
                :listenScroll="listenScroll"
                :probe-type="probeType"
                @scroll="scroll"
                :data="games">
          <div class="game_boxs">
            <div class="games">
              <div class="tit">ABC</div>
                <div class="game_items">
                    <div class="game" v-for="(item,index) in games" :key="index">
                        <image class="game_icon" lazy-load="true" :src="item.imgsrc" />
                        <h2 class="game_name">{{item.name}}</h2>
                    </div>
                </div>
            </div> 
          </div>
        </scroll>
        </div> -->
        <div class="letters"
             v-if="!showAll"
             @touchstart="onShortcutTouchStart" @touchmove.stop.prevent="onShortcutTouchMove">
          <ul>
              <li v-for="(item, index) in letters" :key="index" @click="touchLetter(item,index)">{{item}}</li>
          </ul>
      </div>
    </div>
</template>
<script>
import Scroll from "./scroll.vue";
export default {
  data() {
    return {
      showAll: 0,
      curIndex: 0,
      toView: "ABC",
      game: [
        "全部",
        "热门游戏",
        "日系游戏",
        "女性向游戏",
        "无线游戏",
        "武侠游戏",
        "热门游戏",
        "热门游戏"
      ],
      games: [
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        }
      ],
      gamedef: [
        {
          name: "ddddddd",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "ddddddd",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dddddd",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dddddd",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "ddddddd",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dddd",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        },
        {
          name: "dsdfsdfs",
          imgsrc: "http://p2.qhimgs4.com/t01b0a970f646f800d2.webp"
        }
      ],
      letters: ["ABC", "DEF", "GHI", "JKL", "MNO", "PQR", "STU", "VW", "XYZ"]
    };
  },
  mounted() {
    this.calculateHeight()
  },
  methods: {
    getGameInfo(index) {
      this.curIndex = index;
      this.showAll = index;
    },
    touchLetter(item, index) {
      this.toView = item;
      console.log(item);
    },
    calculateHeight() {
        var query = wx.createSelectorQuery();
        this.listHeight = [];
        const list = query.select('.game_group');
        console.log(list.length);
        
        let height = 0;
        this.listHeight.push(height);
        for (let i = 0; i < list.length; i++) {
        let item = list[i];
        height += item.clientHeight;
        this.listHeight.push(height);
        }
    }
  }
};
</script>
<style lang="scss" scoped>
.swiper_container {
  position: relative;
  .letTit {
    position: absolute;
    top: 104rpx;
    left: 0;
    right: 0;
    z-index: 9;
    padding-left: 30rpx;
    font-size: 20rpx;
    line-height: 50rpx;
    background: #f0f0f0;
  }
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
  .game_groups {
    position: relative;
    width: 100%;
    height: 100%;
    overflow: hidden;
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
        .game_icon {
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
  .letters {
    position: fixed;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
    z-index: 10;
    li {
      height: auto;
      width: 18rpx;
      font-size: 20rpx;
      line-height: 1;
      word-wrap: break-word;
      margin-bottom: 30rpx;
      text-align: center;
      padding: 0 10rpx;
      padding-right: 25rpx;
      &.cur{
          color: #42baa1;
      }
    }
  }
}
</style>
