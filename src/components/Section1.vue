<template>
  <section class="container">
        <div class="row">
            <div class="col-12 p-2" v-for="(film, index) in charactersList" :key="`film-${index}`">
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
import Card from '@/components/Card.vue';


export default {
    name: 'Section1',
    components: {
        Card,
    },
    props: {
        charactersList: Array
    },
    
}
</script>

<style scoped lang="scss">

</style>