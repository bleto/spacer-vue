<template>
  <div class="app">
    <header class="header">
      <nav class="nav">
        <router-link to="/" class="link logo">Spacer</router-link>
        <router-link to="/about" class="link about">@bout</router-link>
      </nav>
    </header>
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,700');
  *{ 
    box-sizing: border-box
  }
  body{
    margin:0;
    padding:0;
    font-family: 'Montserrat', sans-serif;
  }
  .app{
    margin: 0;
    width: 100%;
    height: 100vh;
    position: relative;
    background: url('./assets/bg.jpg') 0 40% / cover no-repeat;

    .header{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 40px;

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
