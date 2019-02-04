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

                        <!--<v-flex is="draggable"
                            v-for="item in 10" :key="item" offset-xs1 xs2 sm5 md3>

                          <v-card
                          >
                            test
                          </v-card>
                        </v-flex>-->
<!--
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
            </draggable>-->

           <!-- <draggable
                v-if="selectedItemGroup === 'Text and Images'"
                v-model="listOfTextAndImages"
                :options="draggableOption('textAndImages')">
              <div class="containerForItem" v-for="(Item, Index) in listOfTextAndImages" :key="Index">
                <img :src="Item.src">
                <div>
                {{Item.name}} {{Index}}
                </div>
              </div>
            </draggable>-->


            <draggable
            class="containerForItems"
            v-model="tempList"
            :options="getOption(selectedItemGroup)">

                <v-flex
                    v-for="(Item, Id) in tempList" :key="Id" xs6
                >

                  <v-card >
                    <v-img v-if="(selectedItemGroup === 'Images')     || (selectedItemGroup === 'Text and Images')" :src="Item.src">  </v-img>
                    <v-card-text v-if="(selectedItemGroup === 'Text') || (selectedItemGroup === 'Text and Images')"> {{Item.name}} </v-card-text>
                  </v-card>
                </v-flex>

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
        {name: 'letter-i', src: require('../assets/alphavite/letter-i.png')},
        {name: 'letter-j', src: require('../assets/alphavite/letter-j.png')},
        {name: 'letter-k', src: require('../assets/alphavite/letter-k.png')},
        {name: 'letter-l', src: require('../assets/alphavite/letter-l.png')},
        {name: 'letter-m', src: require('../assets/alphavite/letter-m.png')},
        {name: 'letter-o', src: require('../assets/alphavite/letter-o.png')},
        {name: 'letter-p', src: require('../assets/alphavite/letter-p.png')},
        {name: 'letter-q', src: require('../assets/alphavite/letter-q.png')},
        {name: 'letter-r', src: require('../assets/alphavite/letter-r.png')},
        {name: 'letter-s', src: require('../assets/alphavite/letter-s.png')},
        {name: 'letter-t', src: require('../assets/alphavite/letter-t.png')},
        {name: 'letter-u', src: require('../assets/alphavite/letter-u.png')},
        {name: 'letter-v', src: require('../assets/alphavite/letter-v.png')},
        {name: 'letter-w', src: require('../assets/alphavite/letter-w.png')},
        {name: 'letter-x', src: require('../assets/alphavite/letter-x.png')},
        {name: 'letter-y', src: require('../assets/alphavite/letter-y.png')},
        {name: 'letter-z', src: require('../assets/alphavite/letter-z.png')},
      ],

      listOfTextAndImages:[
        {name: 'letter-a', src: require('../assets/alphavite/letter-a.png')},
        {name: 'letter-b', src: require('../assets/alphavite/letter-b.png')},
        {name: 'letter-c', src: require('../assets/alphavite/letter-c.png')},
        {name: 'letter-d', src: require('../assets/alphavite/letter-d.png')},
        {name: 'letter-e', src: require('../assets/alphavite/letter-e.png')},
        {name: 'letter-f', src: require('../assets/alphavite/letter-f.png')},
        {name: 'letter-g', src: require('../assets/alphavite/letter-g.png')},
        {name: 'letter-h', src: require('../assets/alphavite/letter-h.png')},
        {name: 'letter-i', src: require('../assets/alphavite/letter-i.png')},
        {name: 'letter-j', src: require('../assets/alphavite/letter-j.png')},
        {name: 'letter-k', src: require('../assets/alphavite/letter-k.png')},
        {name: 'letter-l', src: require('../assets/alphavite/letter-l.png')},
        {name: 'letter-m', src: require('../assets/alphavite/letter-m.png')},
        {name: 'letter-o', src: require('../assets/alphavite/letter-o.png')},
        {name: 'letter-p', src: require('../assets/alphavite/letter-p.png')},
        {name: 'letter-q', src: require('../assets/alphavite/letter-q.png')},
        {name: 'letter-r', src: require('../assets/alphavite/letter-r.png')},
        {name: 'letter-s', src: require('../assets/alphavite/letter-s.png')},
        {name: 'letter-t', src: require('../assets/alphavite/letter-t.png')},
        {name: 'letter-u', src: require('../assets/alphavite/letter-u.png')},
        {name: 'letter-v', src: require('../assets/alphavite/letter-v.png')},
        {name: 'letter-w', src: require('../assets/alphavite/letter-w.png')},
        {name: 'letter-x', src: require('../assets/alphavite/letter-x.png')},
        {name: 'letter-y', src: require('../assets/alphavite/letter-y.png')},
        {name: 'letter-z', src: require('../assets/alphavite/letter-z.png')},
        {name: 'kote', src: require('../assets/1.png')},
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


    /*draggableOption(groupName){
      //let option =
      return{
        group:{
          name: groupName,
          pull:  this.enableDragging? 'clone': false,
          put: false  // Ничего не принимает
        },
        animation: 300,
        sort: this.enableSorting
      }
    },*/

    getOption(groupName){
      return{
            group:{
              name: groupName,
              pull:  this.enableDragging? 'clone': false,
              put: false  // Ничего не принимает
              },
            animation: 300,
            sort: this.enableSorting
          }

    },


  },

  watch:{
    selectedItemGroup:function() {
      switch (this.selectedItemGroup) {
        case('Text'):             {this.tempList = this.listOfText} break;
        case('Images'):           {this.tempList = this.listOfImages} break;
        case('Text and Images'):  {this.tempList = this.listOfTextAndImages} break;
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

  .containerForItems{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-evenly;
    align-items: baseline;
    width: 100%;
    height: auto;

  }

  .item{

  }

  .switchClass{

  }


</style>
