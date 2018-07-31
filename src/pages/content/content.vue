<template>
  <div class="container">
    <web-view :src="viewSrc"></web-view>
  </div>
</template>

<script>
export default {
  props:{
    viewSrc:{
      type: String,
      default:''
    }
  },
  onShow() {
    console.log(this.$root.$mp.query.src);
    // this.viewSrc = 'http://www.baidu.com/?word=123'
    //  + this.$root.$mp.query.id
    this.viewSrc = this.$root.$mp.query.src;
  }
};
</script>
