<template>
  <div class="searchWrapper">
      <input name="search"  id="search" v-model="searchValue" @input="handleInput"/>
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{item.data[0].description}}</p>
        </li>
      </ul>
  </div>
</template>
<script>
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  
  const API = 'https://images-api.nasa.gov/search';
  export default {
    name: 'SearchInput',
    data() {
      return {
        searchValue: '',
        results: []
      };
    },
    methods: {
      handleInput: debounce(function() {
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
  .searchWrapper{
    display: flex;
    flex-direction: column;
    width: 250px;

    input{
      height: 30px;
      border: 0;
      background: none;
      border-bottom: 1px solid black
    }
  }
</style>