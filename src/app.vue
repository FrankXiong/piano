<template>
  <div class="container">
    <Music></Music>
    <KeyBoard></KeyBoard>
  </div>
</template>

<script>
  import KeyBoard from './components/keyboard.vue';
  import Music from './components/music.vue';
  export default {
    name: 'app',
    components: {
      KeyBoard,
      Music
    }
  };
</script>
<style lang="scss" scoped>
  .container {
    margin: 10px;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }
</style>
