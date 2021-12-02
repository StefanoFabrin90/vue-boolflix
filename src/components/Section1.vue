<template>
    <section class="section">
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 col-lg-2 p-3" v-for="item in charactersList" :key="`item-${item.id}`">
                <ul class="list p-3">
                    <!-- card-list film-->
                    <Card
                        class="item"
                        :Image="item.poster_path"
                        :title="item.title ? item.title : item.name"
                        :titleOriginal="item.original_title ? item.original_title : item.original_name "
                        :overview  ="item.overview "
                        :voto="item.vote_average"
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
        charactersList: Array,
    },
    
}
</script>

<style scoped lang="scss">
.list {
    font-size: 12px;
}
</style>