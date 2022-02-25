<template>
    <div class="containerBox">
        <div v-if="start == true">
            <div class="row">
                <div class="box"
                    v-for="(album, index) in albumFiltrati"
                    :key="index.id">
                    <CardAlbum :album="album"></CardAlbum>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import CardAlbum from "./partials/CardAlbum.vue"

import axios from 'axios'

export default {
    name:"ContainerAlbum",
    props: {
        soluzione: String
    },

    components: {
        CardAlbum
    },

    data() {
        return {
            arreyAlbum: [],
            genreAlbum: [],
            apiAlbum: "https://flynn.boolean.careers/exercises/api/array/music",
            start: false,
        }
    },

    methods: {
        getAlbum() {

            axios.get(this.apiAlbum)
            .then((risultato) => {
                this.arreyAlbum = risultato.data.response;
                this.start = true

                for(let i = 0; i < this.arreyAlbum.length; i++) {

                    if(!this.genreAlbum.includes(this.arreyAlbum[i].genre)) {

                    this.genreAlbum.push(this.arreyAlbum[i].genre);
                    }
                }
            })

            .catch(function (error) {
                console.log(error);
            });
        }
    },

    created() {
        this.getAlbum();
        
    },

    mounted() {
        this.$emit('generi', this.genreAlbum)
    },

    computed: {
        albumFiltrati() {
            if (this.soluzione == '') {
                return this.arreyAlbum
            } else {
                return this.arreyAlbum.filter(item => {
                    return item.genre.includes(this.soluzione)
                });
            }
        }
    }
}
</script>

<style lang="scss" scoped>

    .containerBox{
        margin: 0;

        .row{
            height: 90vh;
            margin: 0;
            display: flex;
            justify-content: center;
            background-color: #1e2d3b;
            padding: 40px 300px;
        }

        .box{
            width: calc(100% / 6);
            text-align: center;
            background-color: #2e3a46;
            padding: 15px;
            margin: 10px;
            height: 250px;
        }

        #red{
            height: 300px;
            background-color: red;
        }
    }
</style>