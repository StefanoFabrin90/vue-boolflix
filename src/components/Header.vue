<template>
<section class="section-header d-md-flex align-items-center justify-content-between p-3">
    <nav class="navbar">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSh2ThugbZoENg5Q4LhoDlov2oxigCTiSpNzA&usqp=CAU">
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
    img {
        width: 250px;
    }
    .search {
        width: 350px;
        height: 30%;
    }
}
</style>