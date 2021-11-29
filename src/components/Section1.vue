<template>
  <section class="container">
        <div class="row">
            <div class="col-12 p-2" v-for="(film, index) in ListFilm" :key="`film-${index}`">
                <ul>
                    <!-- card-list -->
                    <Card
                        :title="film.title"
                        :titleOriginal="film.original_title"
                        :language="film.original_language"
                        :voto="film.vote_average"
                    />
                </ul>
            </div>
            
        </div>
  </section>
</template>

<script>
import axios from 'axios';
import Card from '@/components/Card.vue';


export default {
    name: 'Section1',
    components: {
        Card,
    },
    data() {
        return {
            ListFilm: null,
        };
    },
    created() {
        this.createListFilm();
    },
    methods: {
        createListFilm() {
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=c1a413784f6a50ef28c93b5091815f3e&query=star wars')
            .then(result => {
                console.log(result.data.results);
                this.ListFilm = result.data.results;
            })
            .catch(err => console.log(err));
        }
    },
}
</script>

<style scoped lang="scss">

</style>