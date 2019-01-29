<template>
  <div>
    <v-app>
      <v-layout justify-start fill-height>

        <ListOfItem style="width: 400px"/>
        <MainPage style="width: calc(100% - 400px);"/>

      </v-layout>
    </v-app>
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
  i.v-icon.material-icons.theme--light {
    border-color: rgba(60,60,60,.5);
    border-style: solid;
    border-width: 3px 3px 0 0;
    content: "";
    display: inline-block;
    height: 10px;
    width: 10px;
    vertical-align: text-top;
    transform: rotate(133deg);
    box-sizing: inherit;
  }

  i.v-icon.material-icons.theme--light.primary--text {
    border-color: rgba(60,60,60,.5);
    border-style: solid;
    border-width: 3px 3px 0 0;
    content: "";
    display: inline-block;
    height: 10px;
    width: 10px;
    vertical-align: text-top;
    transform: rotate(315deg);
    box-sizing: inherit;
  }
  
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
