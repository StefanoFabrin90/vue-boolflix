<template>
  <div id="app">
    <!-- Header -->
    <Header 
      @performSearch="createListFilm"
    />

    <!-- main -->
    <main>
      <!-- section-1 -->
      <Section1 
        :charactersList="ListFilm"
        :charactersListTv="ListSerieTv"
      />
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
            ListSerieTv: null,
            searchText:'',
      };
  },
  methods: {
    createListFilm(title) {
      console.log(title);
      this.searchText = title;
      const Url = 'https://api.themoviedb.org/3/';

      axios.get(Url,{
          params: {
            api_key: 'c1a413784f6a50ef28c93b5091815f3e',
            query: title,
          }
        }
      )
      .then(result => {
          console.log(result.data.results);
          if(title === 'search/movie') {
            this.ListFilm = result.data.results
          } else if (title === 'search/tv') {
            this.ListSerieTv = result.data.results
          }
      })
      .catch(err => console.log(err));
    },
  },
}
</script>

<style lang="scss">

</style>
