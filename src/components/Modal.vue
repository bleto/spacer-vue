<template>
  <div class="outerWrapper">
    <div class="innerWrapper">
      <div class="photo">
          <img :src="photo" />
      </div>
      <div class="desc">
        <h2 class="title"> {{title}} </h2>
        <p class="desc">
          {{desc}}
        </p>
      </div>
    </div>
    <div class="close" @click="$emit('closeModal')"/>
  </div>
</template>
<script>
  export default {
    name: 'Modal',
    props:{
      item:{
        type: Object,
        required: true
      }
    },
    data() {
      return {
        photo: null,
        title: null,
        desc: null
      };
    },
    mounted(){
      this.photo = this.item.links[0].href;
      this.title = this.item.data[0].title;
      this.desc = this.item.data[0].description.substring(0,200);
    }
  };
</script>

<style lang="scss" scoped>
  .outerWrapper{
    background: #f6f6f6;
    max-width: 100%;
    height: 100vh;
    position: fixed;
    top:0;
    left:0;
    color: #333;

    @media (min-width: 1024px ) {
      max-width: 70%;
      height: 60%;
      left: 0;
      right: 0;
      top:0;
      bottom: 0;
      margin: auto;
      box-shadow: 0 30px 30px -10px rgba($color: #000000, $alpha: 0.4)
    }
  }
  .close{
    position: absolute;
    top: 0;
    right: 0;
    width:30px;
    height: 30px;
    padding: 30px;
    cursor: pointer;

    &::after, &::before{
      position: absolute;
      content: '';
      top:30px;
      right: 20px;
      width: 20px;
      height: 2px;
      background: black;
      display: block;
    }
    &::after{
      transform: rotate(45deg)
    }
    &::before{
      transform: rotate(-45deg)
    }
  }
  .innerWrapper{
    display: flex;
    height: 100%;
    padding: 50px;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    .photo{
      max-width: 90%;
      height: auto;
      background: black;

      img{
        width: 100%;
      }
    }
    @media (min-width: 1024px ) {
      flex-direction: row;
      .photo{
        min-width: 35%;
        max-width: 30%;
        margin-right: 20px;
      }
    }

  }
</style>