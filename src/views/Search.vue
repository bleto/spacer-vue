<template>
  <main class="wrapper">
    <Claim />
    <SearchInput v-model="searchValue" @input="handleInput"/>
  </main>
</template>

<script>
  import Claim from '@/components/Claim.vue';
  import SearchInput from '@/components/SearchInput.vue';
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  
  const API = 'https://images-api.nasa.gov/search';

  export default {
    name: 'Search',
    components:{
      Claim,
      SearchInput
    },
    data() {
      return {
        searchValue: '',
        results: []
      };
    },
    methods: {
      handleInput: debounce(function() {
        console.log(this.searchValue)
        axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((resp) => {
          this.results = resp.data.collection.items;
        }).catch( err => {
          console.error(err);
        })
      },500)
    }
  };
</script>
<style lang="scss" scoped>
  .wrapper{
    margin: 0;
    width: 100%;
    min-height: 100vh;
    padding: 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>

