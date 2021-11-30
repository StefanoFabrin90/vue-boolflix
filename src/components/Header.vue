<template>
<section class="container section-header">
    <div class="input-group mb-3 search">
        <input 
            type="text" 
            placeholder="Inserisci la tua Ricerca"
            class="form-control" 
            aria-label="Sizing example input" 
            aria-describedby="inputGroup-sizing-default"
            v-model.trim="searchText"
            @keyup.enter="$emit('performSearch', searchText)"
        />
        <button 
            type="submit" 
            class="btn btn-secondary"
            @click.prevent="$emit('performSearch', searchText)"
        >   
            Search
        </button>
    </div>
</section>
    
</template>

<script>
export default {
    name:'Header',
    data() {
        return {
            searchText:'',
        }
    },
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