<template>
    <div>
        <li>Titolo: {{ titleTV }}</li>
        <li>Titolo Originale: {{ titleOriginalTV }}</li>
        <li>Lingua:
            <img v-if="flag" :src="require(`../assets/${languageTV}.png`)" :alt="languageTV">
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
            return this.getFlag.includes(this.languageTV)
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