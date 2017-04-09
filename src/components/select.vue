<template>
  <el-radio-group v-model="musicSelected">
    <el-radio-button v-for="item in musicList" :label="item"></el-radio-button>
  </el-radio-group>
</template>

<script>
  export default {
    data () {
      return {
        musicSelected: '茉莉花',
        musicList: [
          '茉莉花',
          '小星星',
          '童话'
        ]
      };
    }
  }
</script>
