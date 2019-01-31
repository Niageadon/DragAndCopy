<template>
  <v-app>

    <ListOfItems />
    <ToolBar/>
    <v-layout justify-start>
        <v-content>

        <MainPage style="height: 3000px;"></MainPage>
       </v-content>v
      </v-layout>
  </v-app>
</template>

<script>
import ListOfItems from "./components/ListOfItems";
import MainPage from "./components/MainPage";
import ToolBar from "@/components/Item/ToolBar";

export default {
  name: 'App',
  components: {
    ToolBar,
    MainPage,
    ListOfItems,
  },
  data () {
    return {
      //
    }
  }
}
</script>
