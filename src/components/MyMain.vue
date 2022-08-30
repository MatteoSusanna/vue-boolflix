<template>
  <main>
    <div class="cards" v-for="(film, indice) in getFilm" :key="indice">
        <div class="card">
            <div class="titolo">{{film.title}}</div>
            <div class="titolo-originale">{{film.original_title}}</div>
            <div class="lingua">{{film.original_language}}</div>
            <div class="Voto">{{film.vote_average}}</div>
        </div>
    </div>
  </main>
</template>

<script>
export default {
    nome: 'MyMain',
    data(){
        return{
            
        }
    },
    props:{
        getFilm: Array
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