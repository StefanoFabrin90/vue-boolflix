<template>
    <div class="card p-5">
        <img 
            v-if="Image !== null"
            :src="`https://image.tmdb.org/t/p/w185${Image}`" 
            :alt="title"
        />
        <img
            class="notfound"
            v-else
            src="https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg" 
            :alt="title"
        />
        <ul class="list">
            <li><span>Titolo:</span>  {{ title }}</li>
            <li><span>Titolo Originale:</span> {{ titleOriginal }}</li>
            <li>{{ overview }}</li>
            <li class="voto">
                <i
                    v-for="(n, i) in stars"
                    :key="`voto-${i}`"
                    class="fas fa-star icon"
                ></i>
                <i
                    v-for="(n, i) in 5 - stars"
                    :key="`empty-${i}`"
                    class="far fa-star icon"
                ></i>
            </li>
        </ul>
        
    </div>
</template>

<script>
export default {
    name: 'CardList',
    props: {
        Image: String,
        title: String,
        titleOriginal: String,
        overview: String,
        voto: Number,
    },
    data() {
        return {
            getFlag: ['it', 'en'],
        }
    },
    computed: {
        flag() {
            return this.getFlag.includes(this.language)
        },
        stars() {
            return Math.ceil(this.voto / 2);
        }
    }
    
}
</script>

<style scoped lang="scss">
.flag {
    height: 30px;
    width: 40px;
}
.notfound {
    width: 185px;
}
.list {
    li {
        list-style: none;
        padding: 3px;
        span {
            text-transform: uppercase;
            text-decoration: underline;
            font-size: 15px;
        }
    }
}
</style>