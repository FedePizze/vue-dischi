<template>
    <div class="containerBox">

        <div id="logoBox">
            <LogoHeader></LogoHeader>

            <select id="select" @change="filtraGenere($event)">
                <option value="">Scegli un genere</option>
                <option v-for="(elemento, index) in generi" :key="index" :value="elemento">{{elemento}}</option>
            </select>
        </div>
    </div>
</template>

<script>
import LogoHeader from "./partials/LogoHeader.vue"

export default {
    name: 'HeaderAlbum',
    props: {
        generi: Array
    },

    components: {
        LogoHeader
    },

    data() {
        return{
            genere: ''
        }
    },

    methods: {
        filtraGenere($event) {
            this.genere = ''
            this.genere = $event.target.value
            console.log($event.target.value)

            this.$emit('genereScelto', this.genere)
        }
    },

    mounted() {
        this.$emit('genereScelto', this.genere)
    },
}
</script>

<style lang="scss" scoped>

    .containerBox{
        height: 10vh;
        margin: 0;

        #logoBox{
            height: 100%;
            width: 100%;
            background-color: #2e3a46;
            display: flex;
            justify-content: space-between;
            align-items: center;

            #select{
                height: 30px;
                padding: 0px 20px;
                margin-right: 20px;
                border-radius: 15px;
            }
        }
    }
</style>