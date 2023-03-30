<template>

  <AppHeader title="Rick and Morty App" ></AppHeader>

  <main>
    <AppSearch @doSearch="getCharacters"/>
    <ResultMessage />
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
  import ResultMessage from './components/ResultMessage.vue';

  export default {
    components: {
      AppHeader,
      CharactersList,
      AppSearch,
      Loading,
      ResultMessage
    },
    data() {
      return {
        store
      }
    },
    methods: {
      getCharacters() {

        //?chiave=valore&altrachiave=altrovalore

        let urlApi = 'https://rickandmortyapi.com/api/character';

        if (store.search.length > 0) {
          urlApi += `?name=${store.search}`;
        }

        axios.get(urlApi)
        .then(response => {
          this.store.charactersList = response.data.results;
          this.store.loading = false;
        })
        .catch(err => {
          console.log(err.response.status);
          this.store.charactersList = [];
          this.store.loading = false;
          console.log('La ricerca non ha dato risultati');
        })

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