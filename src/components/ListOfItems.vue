<template>
<div>
  //cont -> flex

<v-navigation-drawer fixed clipped app >

  <v-container style="padding: 12px">
    <h1>First component</h1>
    <v-divider></v-divider>
    <v-flex align-start justify-center column fill-height>
      <v-switch py-1
        :label="`Dragging`"
        :color="'green'"
        v-model="enableDragging"
        class="switchClass"
      ></v-switch>

      <v-switch py-1
        :label="`Sorting`"
        :color="'green'"
        v-model="enableSorting"
        class="switchClass"
      ></v-switch>
    </v-flex>

    <v-flex xs12 d-flex>
        <v-select
            :items="typesOfData"
            label="Outline style"
            outline
            v-model="selectedItemGroup"
        ></v-select>
      </v-flex>

    <v-divider></v-divider>

    <Simplebar class="ListOfItems">
      <v-container grid-list-md >
        <v-layout align-start justify-center row fill-height>

          <v-flex is="draggable"
              v-for="item in 10" :key="item" offset-xs1 xs2 sm5 md3>

            <v-card
            >
              test
            </v-card>
          </v-flex>

            <draggable
                v-if="selectedItemGroup === 'Text'"
                v-model="listOfText"
                :options="draggableOption('Text')">
              <div v-for="(elements, index) in listOfText" :key="index">{{elements.name}}</div>
            </draggable>

            <draggable
                v-if="selectedItemGroup === 'Images'"
                v-model="listOfImages"
                :options="draggableOption('Images')">
              <div class="containerForItem" v-for="(Image, index) in listOfImages" :key="index">
                <img :src="Image.src">
              </div>
            </draggable>

            <draggable
                v-if="selectedItemGroup === 'Text and Images'"
                v-model="listOfTextAndImages"
                :options="draggableOption('textAndImages')">
              <div class="containerForItem" v-for="(Item, Index) in listOfTextAndImages" :key="Index">
                <img :src="Item.src">
                <div>
                {{Item.name}} {{Index}}
                </div>
              </div>
            </draggable>

            <draggable
                v-if="selectedItemGroup === 'Images'"
            >

            </draggable>


            <draggable>


            </draggable>
        </v-layout>
      </v-container>
    </Simplebar>

    </v-container>

</v-navigation-drawer>

  </div>
</template>

<script>
import draggable from 'vuedraggable'
import Simplebar from 'simplebar-vue';
import 'simplebar/dist/simplebar.min.css';

export default {
    components: {
      draggable: draggable,
      Simplebar
    },

  name: 'ListOfItems',
  props: {
    msg: String
  },

  data: function()
  {
    return{
      typesOfData: ['Text', 'Images', 'Text and Images'],

      listOfText:[
        {name:"John"},
        {name:"George"},
        {name:"Paul"},
        {name:"Ringo"} ],

      listOfImages:[
        {name: 'letter-a', src: require('../assets/alphavite/letter-a.png')},
        {name: 'letter-b', src: require('../assets/alphavite/letter-b.png')},
        {name: 'letter-c', src: require('../assets/alphavite/letter-c.png')},
        {name: 'letter-d', src: require('../assets/alphavite/letter-d.png')},
        {name: 'letter-e', src: require('../assets/alphavite/letter-e.png')},
        {name: 'letter-f', src: require('../assets/alphavite/letter-f.png')},
        {name: 'letter-g', src: require('../assets/alphavite/letter-g.png')},
        {name: 'letter-h', src: require('../assets/alphavite/letter-h.png')},

      ],

      listOfTextAndImages:[
        {name: 'device 1', src: require('../assets/1.png')},
        {name: 'device 2', src: require('../assets/2.jpg')},
        {name: 'device 2', src: require('../assets/2.jpg')},
        {name: 'device 2', src: require('../assets/2.jpg')},
        {name: 'device 2', src: require('../assets/2.jpg')},
      ],

      tempList:[ ],






      enableCopy: false,
      enableDragging: true,
      //isDragging: false,
      delayedDragging:false,
      enableSorting: false,
      selectedItemGroup: '',
    }
  },
  methods: {


    draggableOption(groopName){
      //let option =
      return{
        group:{
          name: groopName,
          pull:  this.enableDragging? 'clone': false,
          put: false  // Ничего не принимает
        },
        animation: 300,
        sort: this.enableSorting
      }
    }
  },

  watch:{
    selectedItemGroup:function() {
      switch (this.selectedItemGroup) {
        case('Text'): {this.tempList = this.listOfText} break;
        case('Images'): {this.tempList = this.listOfImages} break;
        case('Text and Images'): {this.tempList = this.listOfTextAndImages} break;
      }
    }

  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


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

  .ListOfItems{
    height: 470px;
  }

  .containerForItem{
    width: 90%;
    height: auto;
    background-color: aquamarine;
    margin-top: 15px;
  }


</style>
