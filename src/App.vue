<template>
  <div id="app">
    <MyHeader @inputSerch="recuperaInput"  />

    <MyMain :getFilm="getFilm" :getSeries="getSeries"/>

  </div>
</template>

<script>
import MyHeader from './components/MyHeader';
import MyMain from './components/MyMain';

import axios from 'axios';



export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain,
  },
  data(){
    return{
      inputPassata: '',
      getFilm: [],
      getSeries:[],
    }
  },
  methods:{
    recuperaInput(recuperaInput){
      if(!recuperaInput == ''){
        this.inputPassata = recuperaInput;

        axios.get('https://api.themoviedb.org/3/search/movie?api_key=976d1d1629fea964df856f00c768c591&query=' + this.inputPassata + '&language=it-IT')
        .then(film =>{
            this.getFilm = film.data.results;
        })

        axios.get('https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=' + this.inputPassata)
        .then(series =>{
          this.getSeries = series.data.results
        })
      }   
    }
  }
}
</script>

<style lang="scss">
@import './styles/general.scss';


</style>
