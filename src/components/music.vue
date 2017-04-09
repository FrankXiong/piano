<template>
  <div>
    <span>乐谱({{musicName}})</span>
    <span class="switch">换一个</span>
    <div class="music">
      <span class="key" :class="{hidden: item == 0}" v-for="item in keys">{{item}}</span>
    </div>
  </div>
</template>

<script>
  import data from '../data.js';
  export default {
    data: function() {
      return {
        musicName: "茉莉花",
        keys: data.musicList.jasmineFlower
      }
    },
    methods: {

    },
    created() {

    }
  };
</script>
<style lang="scss" scoped>
@import "../assets/style/var.scss";
  .music {
    margin-bottom: 20px;
    width: 100%;
    overflow: hidden;
    .key {
      display: inline-block;
      width: 30px;
      height: 40px;
      font-size: 24px;
    }
    .hidden {
      visibility: hidden;
    }
  }
  .switch {
    color: $blue;
    text-decoration: underline;
    float: right;
  }
</style>
