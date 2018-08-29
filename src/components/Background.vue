<template>
  <div class="spacerBackground" />
</template>
<script>
  export default {
    name: 'Background'
  };
</script>

<style lang="scss" scoped>
  .spacerBackground{
    width: 100%;
    height: 100vh;
    position: fixed;
    top:0;
    z-index: -1;
    background: url('../assets/bg.jpg') 0 40% / cover no-repeat;
    &::after{
      content: '';
      position: absolute;
      top:0;
      left:0;
      z-index: 1;
      width: 100%;
      height: 100vh;
      background-color:rgba(0, 0, 0, 0.4);
    }
  }
</style>