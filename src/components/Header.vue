<template>
<section class="container section-header">
    <div class="input-group mb-3 search">
        <input 
            type="text" 
            class="form-control" 
            aria-label="Sizing example input" 
            aria-describedby="inputGroup-sizing-default"
            v-model.trim="searchText"
            @keyup.enter="$emit('performSearch', searchText), clearInput()"
        />
        <button 
            type="submit" 
            class="btn btn-secondary"
            @click.prevent="$emit('performSearch', searchText), clearInput()"
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
    methods: {
        clearInput(){
            this.searchText = '';
            this.$emit('performSearch', this.searchText);
        },
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