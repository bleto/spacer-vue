<template>
  <main class="wrapper">
    <Claim />
    <SearchInput />
  </main>
</template>

<script>
  import Claim from '@/components/Claim.vue';
  import SearchInput from '@/components/SearchInput.vue';

  export default {
    name: 'Search',
    components:{
      Claim,
      SearchInput
    },
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

  }
</style>

