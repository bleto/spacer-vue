<template>
  <main class="wrapper">
    <Background/>
    <h1>Its me !</h1>
    <a href="mailto:p.bletek@gmail.com">p.bletek@gmail.com</a>
  </main>
</template>
<script>
  import Background from '@/components/Background.vue';
  export default {
    name: 'About',
    components:{
      Background
    }
  };
</script>
<style lang="scss" scoped>
  .wrapper{
    margin: 0;
    width: 100%;
    height: 100vh;
    padding: 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    a{
      text-decoration: none;
      color: tomato
    }
  }
</style>
