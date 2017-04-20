<template>
  <div class="board">
    <div :id="key.code" class="key" :class="{active: key.isActive}" v-for="key in keys" @click="play($event)">
      <audio :src="key.audio" preload>
      </audio>
    </div>
  </div>
</template>

<script>
  import data from '../data.js';
  import move from 'move-js';
  export default {
    data: function() {
      return {
        keys: data.keys
      }
    },
    methods: {
      play(e) {
        const dom = e.srcElement.lastChild;
        dom.cloneNode().play();
      },
      press(code) {
        const dDom = document.getElementById(code);
        let moveBack = move(dDom).y(0);
        move(dDom).y(100).then(moveBack).end();
        dDom.lastChild.cloneNode().play();
      }
    },
    created() {
      let that = this;
      document.onkeydown = function(e) {
        that.press(window.event.keyCode)
      }
    }
  };
</script>
<style lang="scss" scoped>
@import "../assets/style/var.scss";
  .board {
    display: flex;
    justify-content: space-around;
    .key {
      width: 9%;
      height: 300px;
      background: $black;
      text-align: center;
      display: flex;
      justify-content: space-between;
      align-items:flex-end;
      .value {
        color: white;
        font-size: 13px;
      }
    }
  }
</style>
