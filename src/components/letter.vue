<template>
    <div class="letter_container">
        <ul>
            <li v-for="(item, index) in letters" :key="index">{{item}}</li>
        </ul>
    </div>
</template>
<script>
export default {
  data() {
    return {
      letters: ["ABC", "DEF", "GHI", "JKL", "MNO", "PQR", "STU", "VW", "XYZ"]
    };
  }
};
</script>
<style lang="scss">
.letter_container{
    position: fixed;
    right: 25rpx;
    top: 50%;
    transform: translateY(-50%);
    li{
        height: auto;
        width: 18rpx;
        font-size: 20rpx;
        line-height: 1;
        word-wrap: break-word;
        margin-bottom: 30rpx;
        text-align: center;
    }
}
</style>
