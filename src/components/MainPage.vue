<template>
    <div class="Panel">

        <h2>List 1 Draggable</h2>
        <draggable v-model="list" class="dragArea" :options="{group:'people'}">
            <div v-for="element in list">{{element.name}}</div>
        </draggable>

        <h2>List 2 Draggable</h2>
        <draggable v-model="list1" class="dragArea" :options="{group:'people'}">
            <!--<div v-for="element in list1">{{element.name}}</div>-->
            <div id="test">John </div>
            <div id="test1"> George</div>
            <div >Paul </div>
            <div > Ringo</div>
        </draggable>

        <h1> Draggable IMG's </h1>
        <draggable v-model="imgList" class="dragArea" :options="{group:'peop'}">
            <div class="box"> </div>
            <img src="../assets/1.png">
            <img src="../assets/1.png">
        </draggable>

    </div>
</template>

<script>

    import draggable from 'vuedraggable'

    export default {
        components: {
            draggable: draggable
        },
        name: "MainPage",

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
                imgList:[
                    {data: encodeURI ('<div class="box"> </div>')},
                    {data: encodeURI ('<img src="../assets/1.png">')},
                    ],
            }
        }
    }

</script>

<style scoped>
    .Panel{
        width: 100%;
        height: 500px;
        background-color: #87798b;
    }

    .box{
        height: 100px;
        width: 100px;
        background-image: url("../assets/1.png");
    }.
         box1{
        height: 100px;
        width: 100px;
        background-image: url("../assets/2.jpg");
    }
    #test{
        background-color: #34408b;
        height: 100px;
        width: 100px;
    }#test1{
        background-color: #8b537a;
     height: 100px;
     width: 100px;
    }
</style>
