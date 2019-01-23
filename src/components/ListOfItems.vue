<template>
  <div class="ListOfItems drag">

    <draggable v-model="list" class="dragArea" :options="{group:'people'}">
      <div  v-for="element in list"   >{{element.name}}   </div>
    </draggable>
    <hr>
    <draggable v-model="list1" class="dragArea" :options="{group:'people'}"  >
      <div  v-for="element in list1">{{element.name}}   </div>
    </draggable>
    <hr>


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

      getOptions(place) {
        let option = {
            sort: true,
            animation: 0,
            group:{
              name:'tags',
              pull: place.cloneable? 'clone' : true,
              put:  place.droppable
            },
            disabled: !place.editable,
            ghostClass: 'ghost'
          }
        console.log('option');
        return  option;
      },
      isDragging: false,
      delayedDragging:false
    }
  },
  methods: {
    onMove ({relatedContext, draggedContext}) {
      console.log('move');
      const relatedElement = relatedContext.element;
      const draggedElement = draggedContext.element;
      return (!relatedElement || !relatedElement.fixed) && !draggedElement.fixed
    },
  }
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

  .ListOfItems{
    background-color: #000000;
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

  .Item{
    width: 90%;
    height: 50px;
    background-color: black;
    align-self: auto;
    margin-top: 10px;
  }

  .ItemDescription{

  }

</style>
