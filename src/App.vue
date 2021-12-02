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
      <!-- section welcome -->
      <section v-else class="d-flex justify-content-center">
        <div class="welcome">
          <h1 class="text-center">welcome</h1>
          <div class="profile">
            <img src="" alt="">
          </div>
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
  .welcome {
    display: flex;
    flex-direction: column;
    align-items: center;
    h1 {
      font-weight: 200;
      text-transform: uppercase;
      margin: 3rem;
    }
    .profile {
      width: 200px;
      height: 200px;
      background-image: url('./assets/logo_small_icon_only_inverted.png');
      background-position: center;
      background-size: 100%;
      border-radius: 50%;
      animation: pulse 1s infinite alternate;
    }
    @keyframes pulse {
      from{
        transform: scale(1);
      }
      to {
        transform: scale(1.2);
      }
    }
  }
}
</style>
