<template>
    <div>
        <h1 class="mtb">SERIES</h1>
        <div class="cards" >
                <div class="card" v-for="(serie, indice) in getSeries" :key="indice">
                    
                    <div class="copertina" v-if="serie.poster_path == null ">
                        <img :src="require('../assets/rotta.png')" alt="">
                        <p class="t-center">Immagine non disponibile</p>
                    </div>

                    <img class="copertina d-block" 
                        :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path " 
                         v-else
                    />
                    
                    <div class="info d-none">
                        <div class="titolo text_center mb"><h3>{{serie.name}}</h3></div>
                        <div class="titolo-originale text_center">{{serie.original_name}}</div>

                        <div class="wrapperor_language">

                            <div class="lingua" v-if="(serie.original_language == 'en')">
                                <img src="../assets/ing.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'it')">
                                <img src="../assets/ita.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'fr')">
                                <img src="../assets/fra.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'ja')">
                                <img src="../assets/ja.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'es')">
                                <img src="../assets/es.png">
                            </div>
                            <div class="lingua" v-else-if="(serie.original_language == 'ko')">
                                <img src="../assets/ko.png">
                            </div>

                            <div class="lingua text_center" v-else>{{serie.original_language}}</div>

                        </div>

                        <div class="punteggio t-center" v-if="calcolaVoto(serie.vote_average) > 0">
                            <i v-for="n in 5" :key="n"
                                class="fa-star" 
                                :class="(n>calcolaVoto(serie.vote_average))?'fa-regular':'fa-solid'">
                            </i>
                        </div>
                        <div class="punteggio t-center" v-else>VALUTAZIONE NON DISPONIBILE</div>

                        <h3 class="text_center">Trama:</h3>
                        <div class="trama text_center">{{serie.overview}}</div>
                    </div>
                </div>
        </div>

    </div>
</template>

<script>
export default {
    nome: 'MySeries',
    props:{
        getSeries: Array,
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
    .text_center{
        text-align: center;
    }
    .d-block{
        display: block;
    }
    .d-none{
        display: none;
    }
    .t-center{
        text-align: center;
    }


    .cards{
            display: flex;
            flex-wrap: wrap;
            color: $text_color;
            width: 1700px;
            margin: 0 auto;
            .card{
                background-color: black;
                height: 400px;
                width: 200px;
                flex-basis: 15%;
                border: 1px solid white;
                overflow: auto;

                .copertina{
                    width: 100%;
                    height: 100%;
                    object-fit: contain;
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
        }

</style>