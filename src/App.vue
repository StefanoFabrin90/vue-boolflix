<template>
  <div id="app">
    <!-- Header -->
    <Header @performSearch="createListFilm"/>

    <!-- main -->
    <main>
      <!-- section-1 -->
      <Section1 :charactersList="ListFilm"/>
    </main>
    
  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue'
import Section1 from '@/components/Section1.vue'

export default {
  name: 'App',
  components: {
    Header,
    Section1,
  },
  data() {
      return {
            ListFilm: null,
            searchText:'',
      };
  },
  methods: {
    createListFilm(title) {
      console.log(title);
      this.searchText = title;

      axios.get('https://api.themoviedb.org/3/search/movie',
        {
          params: {
            api_key: 'c1a413784f6a50ef28c93b5091815f3e',
            query: title,
          }
        }
      )
      .then(result => {
          console.log(result.data.results);
          this.ListFilm = result.data.results;
      })
      .catch(err => console.log(err));
    },
  },
}
</script>

<style lang="scss">

</style>
