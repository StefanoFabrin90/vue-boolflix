<template>
    <div class="card">
        <img 
            v-if="Image !== null"
            :src="`https://image.tmdb.org/t/p/w185${Image}`" 
            :alt="titleTV"
        />
        <img
            class="notfound"
            v-else
            src="https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg" 
            :alt="titleTV"
        />
        <li>Titolo: {{ titleTV }}</li>
        <li>Titolo Originale: {{ titleOriginalTV }}</li>
        <li>Lingua:
            <img class="flag" v-if="flag" :src="require(`../assets/${languageTV}.png`)" :alt="languageTV">
            <span v-else>{{ languageTV }}</span>
        </li>
        <li>Voto: {{ votoTV / 2 }}</li>
    </div>
</template>

<script>
export default {
    name:'CardTv',
    props: {
        Image: String,
        titleTV: String,
        titleOriginalTV: String,
        languageTV: String,
        votoTV: Number,
    },
    data() {
        return {
            getFlag: ['it', 'en'],
        }
    },
    computed: {
        flag() {
            return this.getFlag.includes(this.languageTV)
        },
        vote() {
            return Math.ceil(this.voto / 2);
        }
    }
}
</script>

<style scoped lang="scss">
li {
    padding: 3px;
}
.flag {
    height: 30px;
}
.notfound {
    width: 185px;
}
</style>