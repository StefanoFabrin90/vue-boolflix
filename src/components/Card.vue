<template>
    <div class="cardlist">
        <div class="cover">
            <img
                class="w-100"
                v-if="Image !== null"
                :src="`https://image.tmdb.org/t/p/w185${Image}`" 
                :alt="title"
            />
            <img
                class="notfound w-100"
                v-else
                src="https://www.publicdomainpictures.net/pictures/280000/velka/not-found-image-15383864787lu.jpg" 
                :alt="title"
            />
        </div>
        <div class="list">
            <ul>
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
.cardlist {
    cursor: pointer;
    position: relative;
    &:hover .list {
        display: block;
    }
    &:hover img {
        filter: blur(var(--value, 1rem));
        transition: filter 1.5s;
    }   
    .cover {
        img {
            height: 400px
        }
    }
    .list {
        color: red;
        font-weight: 700;
        position: absolute;
        overflow-y: auto;
        display: none;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        ul {
            padding: 0;
        }
        li {
            list-style: none;
            padding: 5px;
            span {
                text-transform: uppercase;
                text-decoration: underline;
                font-size: 15px;
            }
            i {
                color: gold;
            }
        }
    }
}
</style>