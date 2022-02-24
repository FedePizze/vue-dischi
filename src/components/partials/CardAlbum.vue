<template>
    <div>
        <img :src="album.poster" alt="">
        <h2>{{album.title}}</h2>
        <h4>{{album.author}}</h4>
        <h4>{{album.year}}</h4>
    </div>
</template>

<script>
export default {
    name: "CardAlbum",
    props: {
        "album": Object
    }
}
</script>

<style lang="scss" scoped>
    
    img{
        width: 100%;
    }
    
    h2{
        font-size: 15px;
        font-weight: 700;
        text-transform: uppercase;
        margin: 10px 0;
        color: white;
    }

    h4{
        font-size: 11px;
        margin: 2px 0;
        color: gray;
    }
    

</style>