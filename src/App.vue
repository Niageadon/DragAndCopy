<template>
 <!-- <v-app>

    <ListOfItems />
    <ToolBar/>

    <v-layout justify-start>
      <v-content>
        <MainPage style="height: 3000px;"></MainPage>
      </v-content>
      </v-layout>
  </v-app>-->

<div class="hide-scroll viewport">
    <ListOfItems />
  <div class="hide-scroll">

    <div>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Doloremque, fugit inventore nihil odio quidem quis
      ratione reiciendis sequi vitae! Cum deserunt dignissimos doloremque enim impedit nemo obcaecati officiis quos
      similique?
    </div>
    <div>Neque nihil nobis numquam odio placeat quisquam voluptates. Ab aut debitis dicta, doloribus, ea expedita fugit
      harum laborum sequi soluta tempora temporibus, voluptates! Corporis eius laborum quos ullam voluptas voluptatem.
    </div>
    <div>Aliquam explicabo magnam quaerat quidem. A accusamus amet dolor illo impedit ipsum, itaque magni nisi, omnis
      quibusdam sint temporibus unde voluptatem! Facilis itaque natus non provident quas quo, sunt voluptatum!
    </div>
    <div>Ab accusamus amet asperiores atque aut cupiditate distinctio dolorem esse est eveniet facilis fuga harum illum
      iste itaque iusto modi molestiae non nostrum obcaecati, quaerat quia quod tempore velit vero.
    </div>

  </div>
</div>



</template>

<script>
import ListOfItems from "./components/ListOfItems";
import MainPage from "./components/MainPage";
import ToolBar from "@/components/Item/ToolBar";
//import VBar from "v-bar";


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


<style>
  .hide-scroll {
    overflow: auto;
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
