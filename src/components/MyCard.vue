<template>
    <div class="wrapper">
        <h2>FILM</h2>
        <div class="cards">
            <div class="card" v-for="(film, indice) in getFilm" :key="indice">

                <img class="copertina d-block" :src="'https://image.tmdb.org/t/p/w342' + film.poster_path " />

                <div  class="info d-none">
                    <div class="titolo text_center">{{film.title}}</div>
                    <div class="titolo-originale text_center">{{film.original_title}}</div>

                    <div class="wrapper_language">

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
        </div>
    </div>
</template>

<script>
export default {
    nome: 'MyCard',
    props:{
        getFilm: Array,
    },
}
</script>

<style lang="scss">
@import '../styles/general.scss';
    .text_center{
        text-align: center;
    }
    .d-block{
        display: block;
    }
    .d-none{
        display: none;
    }

    .cards{
            display: flex;
            flex-wrap: wrap;
            color: $text_color;
            width: 1400px;
            margin: 0 auto;
            .card{
                background-color: black;
                height: 200px;
                width: 200px;
                flex-basis: 15%;
                border: 1px solid red;

                .copertina{
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                
                }
                
                img{
                    width: 100%;
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
            }
        }

</style>