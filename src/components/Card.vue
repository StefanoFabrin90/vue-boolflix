<template>
    <div>
        <li>Titolo: {{ title }}</li>
        <li>Titolo Originale: {{ titleOriginal }}</li>
        <li>Lingua: {{ language }}</li>
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
    }
}
</script>

<style scoped lang="scss">

</style>