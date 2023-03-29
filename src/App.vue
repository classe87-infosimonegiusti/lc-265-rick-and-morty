<template>

  <AppHeader title="Rick and Morty App" ></AppHeader>

  <main>
    <AppSearch />
    <CharactersList />
  </main>

  <Loading />

</template>

<script>
  import axios from 'axios';

  import { store } from './store.js';

  import AppHeader from './components/AppHeader.vue';
  import CharactersList from './components/CharactersList.vue';
  import AppSearch from './components/AppSearch.vue';
  import Loading from './components/Loading.vue';

  export default {
    components: {
      AppHeader,
      CharactersList,
      AppSearch,
      Loading
    },
    data() {
      return {
        store
      }
    },
    methods: {
      getCharacters() {
        axios.get('https://rickandmortyapi.com/api/character')
        .then(response => {
          this.store.charactersList = response.data.results;
          this.store.loading = false;
        });
      }
    },
    created() {
      this.getCharacters();
    }
  }
</script>

<style lang="scss">
  @use './styles/general.scss';

</style>