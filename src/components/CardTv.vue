<template>
    <div>
        <li>Titolo: {{ titleTV }}</li>
        <li>Titolo Originale: {{ titleOriginalTV }}</li>
        <li>Lingua:
            <img v-if="flag" :src="require(`../assets/${language}.png`)" :alt="language">
            <span v-else>{{ languageTV }}</span>
        </li>
        <li>Voto: {{ votoTV }}</li>
    </div>
</template>

<script>
export default {
    name:'CardTv',
    props: {
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
            return this.getFlag.includes(this.language)
        }
    }
}
</script>

<style scoped lang="scss">
li {
    padding: 3px;
}
img {
    height: 30px;
}
</style>