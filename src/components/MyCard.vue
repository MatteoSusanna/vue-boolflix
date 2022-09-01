<template>
    <div class="wrapper">
        <h1 class="mtb">FILM</h1>
        <div class="cards">
            <div class="card" v-for="(film, indice) in getFilm" :key="indice">

                <div class="copertina" v-if="film.poster_path == null ">
                    <img :src="require('../assets/rotta.png')" alt="">
                    <p class="t-center">Immagine non disponibile</p>
                </div>

                <img class="copertina d-block" 
                    :src="'https://image.tmdb.org/t/p/w342' + film.poster_path " 
                    v-else
                />

                <div  class="info d-none">
                    <div class="titolo text_center mb"><h3>{{film.title}}</h3></div>
                    <div class="titolo-originale text_center">{{film.original_title}}</div>

                    <div class="wrapper_language">

                            <div class="lingua" v-if="(film.original_language == 'en')">
                                <img class="bandiera" src="../assets/ing.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'it')">
                                <img class="bandiera" src="../assets/ita.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'fr')">
                                <img class="bandiera" src="../assets/fra.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'ja')">
                                <img class="bandiera" src="../assets/ja.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'es')">
                                <img class="bandiera" src="../assets/es.png">
                            </div>
                            <div class="lingua" v-else-if="(film.original_language == 'ko')">
                                <img class="bandiera" src="../assets/ko.png">
                            </div>
                            <div class="lingua text_center" v-else>{{film.original_language}}</div>
                    </div>
                    
                    <div class="punteggio t-center" v-if="calcolaVoto(film.vote_average) > 0">
                        <i v-for="n in 5" :key="n"
                            class="fa-star" 
                            :class="(n>calcolaVoto(film.vote_average))?'fa-regular':'fa-solid'">
                        </i>
                    </div>
                    <div class="punteggio t-center" v-else>VALUTAZIONE NON DISPONIBILE</div>

                    <h3 class="text_center mtb-10">Trama:</h3>
                    <div class="trama text_center ">{{film.overview}}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    nome: 'MyCard',
    props:{
        getFilm: Array,
    },
    methods:{
        calcolaVoto(voto){
            return Math.ceil(voto / 2);
        }
    }
}
</script>

<style lang="scss">
@import '../styles/general.scss';
    .mb{
        margin-bottom: 20px;
    }
    .mtb-10{
        margin: 10px 0;
    }
    .mtb{
        margin: 30px 0;
    }
    .color_gray{
        color: gray;
    }
    .text_center{
        text-align: center;
    }
    .d-block{
        display: block;
    }
    .d-none{
        display: none;
    }
    .trama{
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        font-size: 13px;
    }

    .cards{
            display: flex;
            flex-wrap: wrap;
            color: $text_color;
            width: 1400px;
            margin: 0 auto;
            .card{
                background-color: black;
                height: 400px;
                width: 200px;
                flex-basis: 15%;
                border: 1px solid white;
                padding: 15px 2px;
                overflow: auto;

                .copertina{
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                }
                
                &:hover .copertina{
                        display: none;
                }
                &:hover .info{
                        display: block;
                }
            }
            .lingua{
                height: 40px;
                width: 40px;
                margin: 20px auto;

                .bandiera{
                    width: 100%;
                    object-fit: cover;
                }
            }
        }

</style>