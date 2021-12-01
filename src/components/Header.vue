<template>
<section class="section-header">
    <nav class="navbar">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">
            <img src="data:image/png;base64,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" alt="" width="70" height="70" class="d-inline-block align-text-top">
            BoolFlix
            </a>
        </div>
    </nav>
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
            class="btn btn-danger"
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
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .search {
        width: 20%;
        height: 30%;
    }
    a {
        display: flex;
        align-items: center;
        color: white;
    }
}
</style>