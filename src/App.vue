<template>
  <div class="app">
    <Background />
    <header class="header">
      <nav class="nav">
        <router-link to="/" class="link logo">Spacer</router-link>
        <router-link to="/about" class="link about">@bout</router-link>
      </nav>
    </header>
    <router-view/>
  </div>
</template>
<script>
import Background from '@/components/Background.vue';
export default {
  name: 'App',
  components:{
    Background
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800');

  $font-weight-light: 300;
  $font-weight-normal: 400;
  $font-weight-bold: 600;
  $font-weight-black: 800;

  *{ 
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  body{
    margin:0;
    padding:0;
    font-family: 'Montserrat', sans-serif;
    color: #fff;
  }
  .app{
    margin: 0;
    width: 100%;
    height: 100vh;
    // background: #bbb;

    .header{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;

      .link{
        font-size: 16px;
        text-decoration: none;
        padding: 20px;
        position: absolute;
        top:0;
        left: 0;

        &.logo{
          color:#000;
          font-weight: 700;
          font-size: 30px;

        } 
        &.about{
          right: 0;
          left: unset;
          color: rgb(236, 12, 61);
        } 
      }
      
    }
  }
</style>
