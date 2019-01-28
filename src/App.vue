<template>
  <div id="app">
    <v-app :dark=darkThemeOn>
      <v-navigation-drawer
          clipped
          v-model="drawer"
          app>
        <v-list>
          <v-list-tile :to="'/'">
            About
          </v-list-tile>
          <v-list-tile :to="'/Localweather'">
            Local weather
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>

      <v-toolbar app fixed clipped-left>
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title>Weather App</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items>
          <v-switch v-model="darkThemeOn"></v-switch>
        </v-toolbar-items>
      </v-toolbar>

    </v-app>



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
