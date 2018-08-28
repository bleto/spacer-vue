<template>
  <main class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input name="search"  id="search" v-model="searchValue" @input="handleInput"/>
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{item.data[0].description}}</p>
        </li>
      </ul>
    </div>
  </main>
</template>

<script>
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  // @ is an alias to /src
  // import HelloWorld from '@/components/HelloWorld.vue';
  const API = 'https://images-api.nasa.gov/search';

  export default {
    name: 'Search',
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
  .wrapper{
    margin: 0;
    width: 100%;
    padding: 30px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .search{
    display: flex;
    flex-direction: column;
    width: 250px;

    label{
      font-family: Arail, sans-serif;
    }
    input{
      font-family: Arail, sans-serif;
      height: 30px;
      border: 0;
      border-bottom: 1px solid black
    }
  }
</style>

