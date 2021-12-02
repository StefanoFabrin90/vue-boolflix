<template>
  <div id="app" class="">
    <!-- Header -->
    <Header 
      @performSearch="createList"
    />

    <!-- main -->
    <main>
      <!-- section-film -->
      <section v-if="ListFilm !== null">
        <Section1 :charactersList="ListFilm"/>
      </section>
      <!-- section-serietv -->
      <section v-if="ListSerieTv !== null">
        <Section1 :charactersList="ListSerieTv"/>
      </section>
      <!-- section title -->
      <section v-else>
        <div>
          <h1>welcome</h1>
          <form action="">
            <input type="text" placeholder="Username">
            <input type="text" placeholder="Username">
            <button type="submit" id="login-button">Login</button>
          </form>
        </div>
      </section>
      
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
body {
  overflow-x: hidden;
  padding-top: 200px;
}
main {
  color: white;
}
</style>
