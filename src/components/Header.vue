<template>
<section class="container section-header">
    <div class="input-group mb-3 search">
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default">
        <button type="button" class="btn btn-secondary">Search</button>
    </div>
</section>
    
</template>

<script>
export default {
    name:'Header'
}
</script>

<style scoped lang="scss">
.section-header {
    background-color: lightgray;
    height: 70px;
    .search {
        padding: 1rem;
    }
}
</style>