<template>
    <div class="Panel">


        <h1>Second component</h1>
        <div id="selector's box" style="margin-left: 5%">
        <v-switch
            :label="`Dragging`"
            :color="'green'"
            v-model="enableDragging"
        ></v-switch>

        <v-switch
            :label="`Copying`"
            :color="'blue'"
            v-model="enableCopy"
        ></v-switch>
        </div>

        <h2>List 1 Draggable</h2>
        <draggable v-model="list" class="dragArea" :options="{group:'people'}">
            <div v-for="(element, Index) in list" :key="Index">{{element.name}} </div>
        </draggable>

        <h2>List 2 Draggable</h2>
        <draggable v-model="list1" class="dragArea" :options="{group:'people'}">
            <!--<div v-for="element in list1">{{element.name}}</div>-->
            <div >Paul </div>
            <div > Ringo</div>
        </draggable>

        <h1> Draggable IMG's </h1>
        <draggable v-model="listItems" class="dragArea" :options="draggableOption('Items')">
            <img :src="listItems[0].src">
            <img :src="listItems[1].src">
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

                listItems:[
                    {name: 'device 1', src: require('../assets/1.png'), width: 10, height: 20},
                    {name: 'device 2', src: require('../assets/2.jpg'), width: 15, height: 30},
                ],

                enableCopy: false,
                enableDragging: true,
            }
        },

        methods:{
            fillImgArray(){
                var img = new Image();
                img.src = "http://yourimage.jpg";

                this.imgList[0].src = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" //splice(0, 1, )
            },
            draggableOption(groopName){
                //let option =
                    return {
                        sort: true,
                    group:{
                        name: groopName,
                        pull: this.enableCopy? 'clone' : true,
                        put: true
                    },
                    //animation: 300
                }
            }
        },

        created(){
            //this.fillImgArray()
        },
        computed:{
            comp1: function () {
              return this.imgList[0].url
            }
        }
    }

</script>

<style scoped>
    .Panel{
        width: 100%;
        height: 800px;
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
