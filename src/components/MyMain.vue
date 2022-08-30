<template>
  <main>
    <div class="cards" >
        <div class="card" v-for="(film, indice) in getFilm" :key="indice">
            <div class="titolo text_center">{{film.title}}</div>
            <div class="titolo-originale text_center">{{film.original_title}}</div>

            <div class="wrapperor_language">

                <div class="lingua" v-if="(film.original_language == 'en')">
                    <img src="../assets/ing.png">
                </div>
                <div class="lingua" v-else-if="(film.original_language == 'it')">
                    <img src="../assets/ita.png">
                </div>
                <div class="lingua" v-else-if="(film.original_language == 'fr')">
                    <img src="../assets/fra.png">
                </div>
                <div class="lingua" v-else-if="(film.original_language == 'ja')">
                    <img src="../assets/ja.png">
                </div>
                <div class="lingua" v-else-if="(film.original_language == 'es')">
                    <img src="../assets/es.png">
                </div>
                <div class="lingua" v-else-if="(film.original_language == 'ko')">
                    <img src="../assets/ko.png">
                </div>

                <div class="lingua text_center" v-else>{{film.original_language}}</div>

            </div>

            <div class="Voto text_center">{{film.vote_average}}</div>
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
    .text_center{
        text-align: center;
    }

    main{
        height: calc(100vh - 100px);
        background-color: $main_color;
        overflow: hidden;
        overflow-y: scroll;
        .cards{
            display: flex;
            flex-wrap: wrap;
            color: $text_color;
            width: 1400px;
            margin: 0 auto;
            .card{
                background-color: black;
                height: 200px;
                flex-basis: 15%;
                border: 1px solid red;
            }
            .lingua{
                height: 40px;
                width: 40px;
                img{
                    width: 100%;
                    object-fit: cover;
                }
            }
        }
    }

</style>