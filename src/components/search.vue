<template>
    <div class="search_container">
        <div class="search_box">
            <p class="srhkw_group">
              <input type="text" class="srhkw" placeholder="输入关键字搜索WIKI" v-model="keyword">
              <i class="close" v-show="keyword" @click="clearkw"></i>
            </p>
            <span class="search_btn" v-text="keyword?'取消':'搜索'"  @click="clearkw"></span>
        </div>
        <!-- 搜索栏结果 -->
        <ul class="srh_list" v-show="srhList">
          <li v-for="(item, index) in srhList" :key="index" @click="srch_oper" >{{item}}</li>
          <!-- <span class="kw">关键字</span> -->
        </ul>
    </div>
</template>
<script>
import {debounce} from '../common/js/util'
export default {
  props:{
    keyword:{
      type: String,
      default: ''
    }
  },
  data() {
    return {
      srhList: []
    };
  },
  mounted() {
    this.srch_oper(this.keyword)
  },
  methods: {
    clearkw() {
      this.keyword = "";
      this.srhList = [];
    },
    // 搜索关键字
    srch_oper(kw) {
      let arr = [];
      this.srhList;
      for (let i = 0; i < arr.length; i++) {
        const item = arr[i];
        this.srhList.push(item.replace(new RegExp(this.keyword, 'gm'), `<rich-text nodes="<span class='kw'>${this.keyword}</span>"></rich-text>`))
      }
      // srhkws.map(item => {
      //   // return item.replace(new RegExp(this.keyword, 'gm'), `<span class="kw">${this.keyword}</span>`);
      //   return item.replace("碧蓝", "1111111");
      // });
      console.log(this.srhList);
    }
  },
  watch: {
    // 监控keyword
    keyword(kw) {
      console.log(kw);
    }
  }
};
</script>
<style lang="scss" scoped>
.search_container {
  position: relative;
  height: 48rpx;
  border: 1px solid #5e5e5e;
  border-radius: 10rpx;
  padding: 20rpx;
  margin: 0 30rpx;
  background: #f7f7f7;
  .search_box {
    display: flex;
    .srhkw_group {
      flex: 1;
      position: relative;
      font-size: 34rpx;
      .srhkw {
        height: 34rpx;
      }
      .close {
        // display: inline-block;
        width: 34rpx;
        height: 34rpx;
        position: absolute;
        top: 8rpx;
        bottom: 0;
        right: 20rpx;
        background: url(../../static/imgs/close.png) no-repeat;
        background-size: 34rpx;
        z-index: 8;
      }
    }
    .search_btn {
      position: relative;
      padding-left: 28rpx;
      font-size: 34rpx;
      font-family: "PingFang";
      &:before {
        content: "|";
        position: absolute;
        left: 0;
      }
    }
  }
  .srh_list {
    position: absolute;
    left: 0;
    right: 0;
    background: #fff;
    margin-top: 20rpx;
    max-height: 500rpx;
    overflow-y: scroll;
    z-index: 9;
    li {
      line-height: 90rpx;
      border-bottom: 1px solid #ddd;
      padding-left: 20rpx;
      color: #999;
      white-space: nowrap;
      text-overflow: ellipsis;
      overflow: hidden;
      .kw {
        display: inline;
        margin: 0;
        color: #000;
      }
    }
  }
}
</style>
