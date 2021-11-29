<template>
    <div>
        <li>Titolo: {{ title }}</li>
        <li>Titolo Originale: {{ titleOriginal }}</li>
        <li>Lingua:
            <img v-if="getlanguageFlag" :src="require(`../assets/${this.language}.png`)" :alt="language">
            <span v-else>{{ language }}</span>
        </li>
        <li>Voto: {{ voto }}</li>
    </div>
</template>

<script>
export default {
    name: 'CardList',
    props: {
        title: String,
        titleOriginal: String,
        language: String,
        voto: Number,
    },
    computed: {
        getlanguageFlag() {
            const filmFlag = ['it', 'en'];
            return filmFlag.includes(this.language) ? true : false;
        },
    },
}
</script>

<style scoped lang="scss">
li {
    padding: 3px;
}
img {
    height: 30px;
    width: 40px;
}
</style>