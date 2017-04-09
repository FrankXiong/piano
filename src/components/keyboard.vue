<template>
  <div class="board">
    <div class="key" :class="{active: key.isActive}" v-for="key in keys" @click="play($event)">
      <audio :id="key.code" :src="key.audio" preload>
        <!-- <source  type="audio/ogg"> -->
      </audio>
    </div>
  </div>
</template>

<script>
  import data from '../data.js';
  export default {
    data: function() {
      return {
        keys: data.keys
      }
    },
    methods: {
      play(e) {
        e.srcElement.lastChild.play();
      },
      press(code) {
        const dDom = document.getElementById(code);
        dDom.cloneNode().play();
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
      height: 50vh;
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
  .active {
    animation-name: bounce;
    transform-origin: center bottom;
    animation-duration: 1s;
    animation-fill-mode: both;
  }
  @keyframes bounce {
    from, 20%, 53%, 80%, to {
      -webkit-animation-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
      animation-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
      -webkit-transform: translate3d(0,0,0);
      transform: translate3d(0,0,0);
    }

    40%, 43% {
      -webkit-animation-timing-function: cubic-bezier(0.755, 0.050, 0.855, 0.060);
      animation-timing-function: cubic-bezier(0.755, 0.050, 0.855, 0.060);
      -webkit-transform: translate3d(0, -30px, 0);
      transform: translate3d(0, -30px, 0);
    }

    70% {
      -webkit-animation-timing-function: cubic-bezier(0.755, 0.050, 0.855, 0.060);
      animation-timing-function: cubic-bezier(0.755, 0.050, 0.855, 0.060);
      -webkit-transform: translate3d(0, -15px, 0);
      transform: translate3d(0, -15px, 0);
    }

    90% {
      -webkit-transform: translate3d(0,-4px,0);
      transform: translate3d(0,-4px,0);
    }
  }
</style>
