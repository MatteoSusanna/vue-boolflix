<template>
  <div id="app">
    <MyHeader @inputSerch="recuperaInput"  />

    <MyMain :inputPassata="inputPassata"/>

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
