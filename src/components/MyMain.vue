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
import axios from 'axios';

export default {
    nome: 'MyMain',
    data(){
        return{
            getFilm: [],
        }
    },
    props:{
        inputPassata: String
    },
    created(){
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=976d1d1629fea964df856f00c768c591&query=' + this.inputPassata + '&language=it-IT')
        .then(film =>{
            this.getFilm = film.data.results;
            console.log(this.getFilm)
        })

        
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