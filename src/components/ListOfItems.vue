<template>
<div>
  //cont -> flex

<v-navigation-drawer fixed clipped app
v-model="drawer"
>

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
            label="Data types:"
            outline
            v-model="selectedItemGroup"
        ></v-select>
      </v-flex>

    <v-divider></v-divider>

    <Simplebar class="ListOfItems">
      <v-container grid-list-md >
        <v-layout align-start justify-center row fill-height>

            <draggable
            class="containerForItems"
            v-model="tempList"
            :options="getOption(selectedItemGroup)">

                <v-flex
                    v-for="(Item, Id) in tempList" :key="Id" xs6
                    style="max-width: 200px"
                >

                  <v-card
                    elevation="10"
                  >
                    <v-img v-if="(selectedItemGroup === 'Images')     || (selectedItemGroup === 'Text and Images')" :src="Item.src">  </v-img>
                    <v-card-title v-if="(selectedItemGroup === 'Text') || (selectedItemGroup === 'Text and Images')"> {{Item.name}} </v-card-title>
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

import { EventBus } from '../bus.js';

// Listen for the i-got-clicked event and its payload.


export default {
    components: {
      draggable: draggable,
      Simplebar,

    },

  name: 'ListOfItems',
  props: {
    msg: String
  },

  created(){
    EventBus.$on('boba', data => {
      //console.log(`Oh, that's nice. It's gotten ${data} clicks! :)`);
      this.drawer = !this.drawer//data работает некорректно, когда drawer сворачивается самостоятельно, потому не используется
    });
  },

  data: function()
  {
    return{
      drawer: true,

      //test: EventBus.$on('boba', this.drawer),

      typesOfData: ['Text', 'Images', 'Text and Images'],

      listOfText:[
        {name:"Abam"},
        {name:"Aduke"},
        {name:"Baako"},
        {name:"Boba"},
        {name:"Bobo"},
        {name:"Biba"},
        {name:"Chaonaine"},
        {name:"Chinelo"},
        {name:"Dada"},
        {name:"Dawud"},
        {name:"Dumaka"},
        {name:"Ebun"},
        {name:"Fabayo"},
        {name:"Folade"},
        {name:"Foluke"},
        {name:"Gamba"},
        {name:"Hasanati"},
        {name:"Hondo"},
        {name:"Ibrahim"},
        {name:"Japera"},
        {name:"Jojo"},
        {name:"Kosoko"},
        {name:"Kukua"},
        {name:"Lateefa"},
        {name:"Lutalo"},
        {name:"Mama"},
        {name:"Monifa"},
        {name:"Njemile"},
        {name:"Obayana"},
        {name:"Pasua"},
        {name:"Ranako"},
        {name:"Rehema"},
        {name:"Salihah"},
        {name:"Sekelaga"},
        {name:"Sisi"},
        {name:"Teleza"},
        {name:"Tulinagwe"},
        {name:"Uchenna"},
        {name:"Walidah"},
        {name:"Yazid"},
        {name:"Zainabu"},
        {name:"Zuberi"},
        ],

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
        {name: 'space', src: require('../assets/alphavite/space.png')},
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
        {name: 'space', src: require('../assets/alphavite/space.png')},
        {name: 'kote', src: require('../assets/1.png')},

      ],

      tempList:[],

      enableCopy: false,
      enableDragging: true,
      //isDragging: false,
      delayedDragging:false,
      enableSorting: false,
      selectedItemGroup: '',
    }
  },
  methods: {

    testFun(a){
      this.test = a;
    },
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
    height: 30vw;
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
