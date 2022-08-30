<template>
  <main>

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
    created(){
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=976d1d1629fea964df856f00c768c591&query=2021&language=it-IT')
        .then(film =>{
            this.getFilm = film
        })
    }
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