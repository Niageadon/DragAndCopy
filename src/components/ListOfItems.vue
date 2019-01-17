<template>
  <div class="ListOfItems">
    <ul class="List">
      <li class="Item" v-for="item in Items">
        {{item}}
        <img src="../assets/logo.png">
        <h3> Some text </h3>
      </li>

    </ul>
  </div>
</template>

<script>
export default {
  name: 'ListOfItems',
          props: {
    msg: String
  },

  data: function()
  {
    return{
      Items:[
        '1',
        '2',
        '3'
      ],
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  ul{
    list-style-type: none;
    padding-left: 0;
    margin: 10px 0 0 0;
  }
  li{
    display: flex;
    justify-content: flex-start;  /* равномерное распределение дочерних элементов */
    align-items: center;
    flex-direction: column;
  }
  img{
    height: 300px;
    width: 90%;
  }
  h3{
    width: 80%;
  }

  .ListOfItems{
    background-color: aqua;
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
    height: 500px;
    background-color: black;
    align-self: auto;
    margin-top: 10px;
  }

  .ItemDescription{

  }

</style>
