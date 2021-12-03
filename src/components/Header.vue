<template>
<section 
    class="section-header fixed-top d-md-flex align-items-center justify-content-between p-2"
>
    <nav class="navbar d-flex">
        <div class="container-fluid">
            <a 
                class="navbar-brand" 
                href="#"
                @click.prevent="$emit('backHome')"
            >
                <img class="imgfirst" src="../assets/logo_large.png">
                <img class="imgsecond" src="../assets/logo_white_large.png">
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
            id="inputbar" 
            aria-label="Sizing example input" 
            aria-describedby="inputGroup-sizing-default"
            v-model.trim="searchText"
            @keyup.enter="$emit('performSearch', searchText)"
        />
        <button 
            type="submit" 
            class="btn btn-danger"
            id="button"
            @click.prevent="$emit('performSearch', searchText)"
        >   
            Search
        </button>
        <button 
            type="submit" 
            class="btn btn-secondary"
            id="button"
            @click.prevent="resetSearch"
        >   
            Reset
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
    methods: {
        resetSearch() {
            this.searchText='';
            //this.$emit('performSearch', this.searchText)
        }
    },
}
</script>

<style scoped lang="scss">
.section-header {
    background-color: #333;
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
    a {
        &:hover .imgsecond {
            display: block;
        }
        &:hover .imgfirst {
            display: none;
        }
    }
    .imgsecond {
        display: none;
    }
    .search {
        width: 380px;
        height: 30%;
        #inputbar {
            border-radius: 0.25rem;
        }
        
        #button {
            margin-left: 10px;
            border-radius: 0.25rem;
        }
    }
    
}
</style>