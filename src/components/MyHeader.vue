<template>
  <header>
    <h1>BOOLFLIX</h1>
    <div class="wrapper-serch">

        <input type="text" 
        v-model="inputSerch"
        @keyup.enter="$emit('inputSerch', inputSerch)"
        placeholder="Cerca..."/>

        <button @click="$emit('inputSerch', inputSerch)">Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
    nome: 'MyHeader',
    data(){
        return{
            inputSerch: ''
        }
    }
}
</script>

<style lang="scss">
@import '../styles/general.scss';

    header{
        height: 100px;
        background-color: $header_color;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 50px;
        h1{
            color: #ff8906;
            font-weight: 500;
        }
        .wrapper-serch{

            input{
                height: 30px;
                margin-right: 10px;
                font-size: 17px;
                padding: 5px;
                border-radius: 5px;
            }
            button{
                height: 30px;
                background-color: #ff8906;
                font-weight: 600;
                padding: 0 10px;
                border-radius: 5px;

                &:hover{
                    outline: 1px solid #ff8906;
                }
            }
        }
    }

</style>