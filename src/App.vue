<template>
  <div id="app">
    <MyHeader @inputSerch="recuperaInput" :inputPassata="inputPassata" />

    <MyMain />

  </div>
</template>

<script>
import MyHeader from './components/MyHeader';
import MyMain from './components/MyMain';

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain,
  },
  data(){
    return{
      inputPassata: '',
    }
  },
  methods:{
    recuperaInput(recuperaInput){
      this.inputPassata = recuperaInput;
    }
  }
}
</script>

<style lang="scss">
@import './styles/general.scss';

</style>
