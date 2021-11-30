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
      this.createListFilm(title)
      this.createListTv(title)
    },

    createListFilm (title) {
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
        this.ListFilm = result.data.results
      })
      .catch(err => console.log(err));
    },

    createListTv (title) {
      this.searchText = title;
      axios.get('https://api.themoviedb.org/3/search/tv',
        {
          params: {
            api_key: 'c1a413784f6a50ef28c93b5091815f3e',
            query: title,
          }
        }
      )
      .then(result => {
        console.log(result.data.results);
        this.ListSerieTv = result.data.results
      })
      .catch(err => console.log(err));
    },
  },
}
</script>

<style lang="scss">

</style>
