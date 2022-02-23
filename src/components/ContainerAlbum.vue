<template>
    <div class="containerBox">

        <dir id="logoBox">
            <!-- <img id="logo" src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png" alt=""> -->
            <LogoHeader></LogoHeader>
        </dir>

        <div v-if="aaa == true">
            <div class="row">
                <CardAlbum
                    v-for="(album, index) in arreyAlbum"
                    :key="index.id"
                    :album="album">
                </CardAlbum>
            </div>
        </div>
    </div>
</template>

<script>
import CardAlbum from "./partials/CardAlbum.vue"
import LogoHeader from "./partials/LogoHeader.vue"

import axios from 'axios'

export default {
    name:"ContainerAlbum",

    components: {
        CardAlbum,
        LogoHeader
    },

    data() {
        return {
            arreyAlbum: [],
            apiAlbum: "https://flynn.boolean.careers/exercises/api/array/music",
            aaa: false
        }
    },

    methods: {
        getAlbum() {

            axios.get(this.apiAlbum)
            .then((risultato) => {
                this.arreyAlbum = risultato.data.response;
                this.aaa = true
                console.log(this.arreyAlbum)
            })

            .catch(function (error) {
                console.log(error);
            });

        }
    },

    created() {
        this.getAlbum();
    }
}
</script>

<style lang="scss" scoped>

    .containerBox{
        height: 100vh;
        margin: 0;

        #logoBox{
            height: 8vh;
            width: 100%;
            background-color: #2e3a46;
        }

        .row{
            height: 92vh;
            margin: 0;
            display: flex;
            justify-content: center;
            background-color: #1e2d3b;
            padding: 40px 300px;
        }
    }
</style>