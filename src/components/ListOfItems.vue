<template>
  <div class="ListOfItems drag">

<drag  :list="someData.list" class="dragArea">

          <div style="color: azure"  v-for="element in someData.list"  v-bind:key="element.name" > 1212 {{ element.name}}   </div>

</drag>

  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
    component: {
        drag: draggable
    },

  name: 'ListOfItems',
  props: {
    msg: String
  },

  data: function()
  {
    return{
      someData: {
        id:[1, 2, 3, 4],
        list:[
          {name:"John"},
          {name:"George"},
          {name:"Paul"},
          {name:"Ringo"} ]
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
