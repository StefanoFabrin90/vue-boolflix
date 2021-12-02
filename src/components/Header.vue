<template>
<section 
    class="section-header fixed-top d-md-flex align-items-center justify-content-between p-2"
>
    <nav class="navbar d-flex">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">
            <img src="../assets/logo_large.png">
            </a>
            <div class="listHeader d-flex">
                <ul 
                    class="list p-sm-2"
                    v-for="(item, index) in listItem" :key="`ietm-${index}`"
                >
                    <li> {{ item.text }}</li>
                </ul>
            </div>
        </div>
        
    </nav>
    <div class="input-group mb-3 search d-flex">
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
            listItem: [
                {
                    text:'Home',
                    url: '#',
                },
                {
                    text:'Serie Tv',
                    url: '#',
                },
                {
                    text:'Film',
                    url: '#',
                },
                {
                    text:'Categoria',
                    url: '#',
                },
                {
                    text:'La mia Lista',
                    url: '#',
                },
            ],
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
    .list {
        list-style: none;
        padding: 2px 5px 0px 0;
        li {
            color: white;
            cursor: pointer;
            //transition: transform .1s;
            &:hover {
                text-decoration: underline;
                color: red;
                text-transform: uppercase;
                //transform: scale(1.1);
            }
        }
    }
    .search {
        width: 350px;
        height: 30%;
    }
}
</style>