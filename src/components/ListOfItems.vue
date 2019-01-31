<template>
<div>
<v-navigation-drawer fixed clipped app hide-overlay>
<h1>First component</h1>

    <v-container>
    <v-flex align-start justify-center column fill-height ml-3>
    <v-switch py-1
        :label="`Dragging`"
        :color="'green'"
        v-model="enableDragging"
    ></v-switch>
    </v-flex>
    </v-container>

    <v-flex xs12 sm6 d-flex>
      <v-select
          :items="items"
          label="Outline style"
          outline
      ></v-select>
    </v-flex>

    <hr>
    <draggable v-model="list1" :options="{group:'people'}"  >
      <div  v-for="(elements, index) in list1" :key="index">{{elements.name}}   </div>
    </draggable>
    <hr>

    <draggable v-model="listItems" :options="draggableOption('Items')">
      <div class="containerForItem" v-for="(Item, Index) in listItems" :key="Index">
        <img :src="Item.src">
        <div>
        {{Item.name}} {{Index}}
        </div>
      </div>
    </draggable>

</v-navigation-drawer>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
    components: {
        draggable: draggable
    },

  name: 'ListOfItems',
  props: {
    msg: String
  },

  data: function()
  {
    return{
      items: ['Foo', 'Bar', 'Fizz', 'Buzz'],

      list:[
        {name:"JOJO"},
        {name:"FFDD"},
        {name:"RRRR"},
        {name:"EEWS"} ],


      list1:[
        {name:"John"},
        {name:"George"},
        {name:"Paul"},
        {name:"Ringo"} ],

      listItems:[
        {name: 'device 1', src: require('../assets/1.png'), width: 10, height: 20},
        {name: 'device 2', src: require('../assets/2.jpg'), width: 15, height: 30},
      ],

      enableCopy: false,
      enableDragging: true,
      isDragging: false,
      delayedDragging:false
    }
  },
  methods: {


    draggableOption(groopName){
      //let option =
      return{
        sort: true,
        group:{
          name: groopName,
          pull:  'clone',
          put: this.enableDragging? true: false
        },
        animation: 300
      }
    }


  },

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>



  .dragArea {
    min-height: 10px;
  }

  ul{
    list-style-type: none;
    padding-left: 0;
    margin: 0 0 0 0;
  }
  li{
    display: flex;
    justify-content: flex-start;  /* равномерное распределение дочерних элементов */
    align-items: center;
    flex-direction: column;
    margin-top: 10px;
    color: azure;
  }
  img{
    height: 300px;
    width: 90%;
  }
  h3{
    width: 80%;
  }



  .List{
    width: 100%;
    height: 100%;
    border: black 10px;
    background-color: blue;
    display: flex;
    justify-content: flex-start;  /* равномерное распределение дочерних элементов */
    align-items: center;
    flex-direction: column;
  }

  .Types{
    width: 90%;
    height: 500px;

  }
  .containerForItem{
    width: 90%;
    height: auto;
    background-color: aquamarine;
    margin-top: 15px;
    min-height: 30px;
  }

  .Item{
    width: 90%;
    height: auto;
    background-color: #d6d6d6;
    align-self: auto;
    margin-top: 10px;
  }


</style>
