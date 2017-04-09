<template>
  <div class="music-panel">
    <div class="music-header">
      <span>乐谱({{music.name}})</span>
      <span v-show="hintVisible" class="hint">*请将屏幕调整为横向</span>
    </div>
    <div class="music">
      <span class="key" :class="{hidden: item == 0}" v-for="item in music.value">{{item}}</span>
    </div>
    <el-dialog title="选择一项" size="full" v-model="dialogVisible">
      <el-radio-group v-model="musicSelected">
        <div class="music-item" v-for="item in musicList">
          <el-radio :label="item.name"></el-radio>
        </div>
      </el-radio-group>
    </el-dialog>
    <span class="switch" @click="dialogVisible = true">换一曲</span>
  </div>
</template>

<script>
  import data from '../data.js';
  export default {
    data: function() {
      return {
        dialogVisible: false,
        hintVisible: false,
        musicSelected: '',
        music: data.musicList[0] || {
          name: '茉莉花',
          value: [
            3,3,5,6,8,8,6,5,0,5,6,5,0,3,3,5,6,8,8,6,5,0,0,5,0,3,2,3,5,0,3,2,1,0,1,2,1,0,3,2,1,2
          ]
        },
        musicList: data.musicList
      }
    },
    created() {
      if (window.screen.orientation.type == "portrait-primary") {
        this.hintVisible = true;
      }
    }
  };
</script>
<style lang="scss" scoped>
@import "../assets/style/var.scss";
.music-panel {
  height: 30vh;
  position: relative;
  margin-bottom: 20px;
  .music-header {
    margin-bottom: 10px;
    .hint {
      font-size: 12px;
      color: $lightGray;
    }
  }
  .music {
    width: 100%;
    overflow: hidden;
    .key {
      display: inline-block;
      width: 30px;
      height: 30px;
    }
    .hidden {
      visibility: hidden;
    }
  }

  .switch {
    color: $blue;
    text-decoration: underline;
    position: absolute;
    right: 10px;
    top: 0;
  }
}
.music-item {
  margin-right: 10px;
  display: inline-block;
}
.el-dialog {
  opacity: 0.95;
}
</style>
