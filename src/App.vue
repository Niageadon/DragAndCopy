<template>
  <div id="app">

    <ListOfItem style="width: 400px"/>
    <MainPage style="width: calc(100% - 400px);"></MainPage>
  </div>
</template>

<script>
import ListOfItems from './components/ListOfItems.vue'
import MainPage from "@/components/MainPage";

export default {
  name: 'app',
  components: {
    MainPage,
    ListOfItem: ListOfItems
  },
  data(){
    return{
      darkThemeOn: true,
      drawer: true
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: flex-start;  /* равномерное распределение дочерних элементов */
  align-items: flex-start;
  flex-direction: row ;
}
</style>
