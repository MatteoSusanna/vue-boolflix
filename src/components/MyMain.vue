<template>
  <main>
    <MyCard :getFilm="getFilm"/>
    <MySeries :getSeries="getSeries"/>
  </main>
</template>

<script>
import MyCard from './MyCard';
import MySeries from './MySeries';

export default {
    nome: 'MyMain',
    components:{
        MyCard,
        MySeries
    },
    props:{
        getFilm: Array,
        getSeries: Array
    },
    created(){

        
    },
}
</script>

<style lang="scss">
@import '../styles/general.scss';

    main{
        height: calc(100vh - 100px);
        background-color: $main_color;
        overflow: hidden;
        overflow-y: scroll;
        
    }

</style>