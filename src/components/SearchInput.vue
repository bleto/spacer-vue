<template>
  <input name="search"  id="search" :value="value" @input="handleChange"/>
</template>
<script>
  export default {
    name: 'SearchInput',
    props: {
      value: {
        type: String,
        required: true
      }
    },
    methods: {
      handleChange(e) {
        this.$emit('input', e.target.value);
      }
    }
  };
</script>

<style lang="scss" scoped>

  input{
    display: flex;
    flex-direction: column;
    width: 250px;
    margin-top:50px;
    height: 30px;
    border: 0;
    background: none;
    text-align: center;
    font-size: 18px;
    color: #fff;
    border-bottom: 1px solid #fff;
    transition: box-shadow .4s ease-out;
    @media (min-width: 1024px) {
      font-weight: 400;
    }

    &:focus{
      outline: none;
      box-shadow: 0 10px 20px -9px rgba(255,255,255,0.5);
    }
  }
</style>