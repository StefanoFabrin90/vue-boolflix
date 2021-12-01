<template>
    <section class="container">
        <div class="row">
            <div class="col-4 p-2" v-for="item in charactersList" :key="`item-${item.id}`">
                <ul class="list h-100">
                    <!-- card-list film-->
                    <Card
                        class="h-100 item"
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
    padding: 1rem;
    font-size: 14px;
}
.item {
    display: flex;
    align-items: center;
}
</style>