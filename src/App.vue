<template>
  <v-app>

    <ListOfItems/>
    <ToolBar/>

    <v-layout justify-start>
      <v-content>
        <MainPage></MainPage>
      </v-content>
      </v-layout>


  </v-app>
</template>

<script>
import ListOfItems from "./components/ListOfItems";
import MainPage from "./components/MainPage";
import ToolBar from "@/components/Item/ToolBar";
import Item from "./components/Item/Item";
//import Simplebar from 'simplebar-vue';
//import 'simplebar/dist/simplebar.min.css';
//import VBar from "v-bar";


export default {
  name: 'App',
  components: {
    Item,
    ToolBar,
    MainPage,
    ListOfItems,
    //Simplebar

  },
  data () {
    return {
      //
    }
  }
}
</script>


<style>
  .scroll {
   width: 200px  ;
    height: 100px;
  }

  .viewport {
    overflow: auto;

    /* Make sure the inner div is not larger than the container
     * so that we have room to scroll.
     */
    max-height: 100%;

    /* Pick an arbitrary margin/padding that should be bigger
     * than the max width of all the scroll bars across
     * the devices you are targeting.
     * padding = -margin
     */
    margin-right: -100px;
    padding-right: 100px;
  }

  .wrapper {
    height: 300px;
    width: 300px;
  }

  .vuebar-element {
    height: 250px;
    width: 100%;
    max-width: 500px;
    background: #dfe9fe;
  }


  .vb > .vb-dragger {
    z-index: 5;
    width: 12px;
    right: 0;
  }

  .vb > .vb-dragger > .vb-dragger-styler {
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-transform: rotate3d(0,0,0,0);
    transform: rotate3d(0,0,0,0);
    -webkit-transition:
        background-color 100ms ease-out,
        margin 100ms ease-out,
        height 100ms ease-out;
    transition:
        background-color 100ms ease-out,
        margin 100ms ease-out,
        height 100ms ease-out;
    background-color: rgba(48, 121, 244,.1);
    margin: 5px 5px 5px 0;
    border-radius: 20px;
    height: calc(100% - 10px);
    display: block;
  }

  .vb.vb-scrolling-phantom > .vb-dragger > .vb-dragger-styler {
    background-color: rgba(48, 121, 244,.3);
  }

</style>
