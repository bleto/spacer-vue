<template>
  <main :class="[{flexStart: step === 1}, 'wrapper' ]">
    <transition name="fade">
      <Background v-if="step === 0"/>
    </transition>
    <Claim v-if="step === 0"/>
    <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
    <div class="results" v-if="results && !loading && step === 1"> 
      <Item v-for="item in results" :item="item" :key="item.data[0].nasa_id" @click.native="handleModalOpen(item)"/>
    </div>
    <Modal v-if="modalOpen" @closeModal="modalOpen = false" :item="modalItem"/>
  </main>
</template>

<script>
  import Claim from '@/components/Claim.vue';
  import SearchInput from '@/components/SearchInput.vue';
  import Background from '@/components/Background.vue';
  import Item from '@/components/Item.vue';
  import Modal from '@/components/Modal.vue';
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  
  const API = 'https://images-api.nasa.gov/search';

  export default {
    name: 'Search',
    components:{
      Claim,
      SearchInput,
      Background,
      Item,
      Modal
    },
    data() {
      return {
        modalOpen: false,
        modalItem: null,
        loading: false,
        step: 0,
        searchValue: '',
        results: []
      };
    },
    methods: {
      handleModalOpen: function(item){
          this.modalOpen = true;
          this.modalItem = item;
      },
      handleInput: debounce(function() {
        this.loading = true;
        console.log(this.searchValue)
        axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((resp) => {
          this.results = resp.data.collection.items;
          this.loading = false
          this.step = 1;
        }).catch( err => {
          console.error(err);
        })
      },500)
    }
  };
</script>
<style lang="scss" scoped>
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s ease;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
  .wrapper{
    margin: 0;
    width: 100%;
    min-height: 100vh;
    padding: 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &.flexStart{
      justify-content: flex-start
    }
  }
  .results{
    margin-top:50px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;

    @media (min-width: 768px) {
      width: 90%;
      grid-template-columns: 1fr 1fr 1fr;
    }
  }
</style>

