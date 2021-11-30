<template>
  <div id="app">
    <!-- Header -->
    <Header 
      @performSearch="createList"
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
    createList(title) {
      this.searchText = title;
      const url = ['search/movie', 'search/tv'];
      const UrlPre = 'https://api.themoviedb.org/3/' + url
      axios.get(UrlPre ,
        {
          params: {
            api_key: 'c1a413784f6a50ef28c93b5091815f3e',
            query: title,
          }
        }
      )
      .then(result => {
          console.log(result.data.results);
          if() {
            this.ListFilm = result.data.results
          } else if () {
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
