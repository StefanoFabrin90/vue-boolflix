<template>
    <section class="container">
        <div class="row">
            <div class="col-12 p-2" v-for="film in charactersList" :key="`film-${film.id}`">
                <ul>
                    <!-- card-list film-->
                    <Card
                        :title="film.title"
                        :titleOriginal="film.original_title"
                        :language="film.original_language"
                        :voto="film.vote_average"
                    />
                </ul>
            </div>
            <div class="col-12 p-2" v-for="item in charactersListTv" :key="`item-${item.id}`">
                <ul>
                    <!-- card-list TV -->
                    <CardTv 
                        :titleTV="item.name"
                        :titleOriginalTV="item.original_name"
                        :languageTV="item.original_language"
                        :votoTV="item.vote_average"
                    />
                </ul>
            </div>
        </div>
    </section>
</template>

<script>
import Card from '@/components/Card.vue';
import CardTv from '@/components/CardTv.vue';


export default {
    name: 'Section1',
    components: {
        Card,
        CardTv,
    },
    props: {
        charactersList: Array,
        charactersListTv: Array,
    },
    
}
</script>

<style scoped lang="scss">

</style>