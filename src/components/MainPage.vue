<template>
    <div class="Panel">

        <h2>List 1 Draggable</h2>
        <draggable v-model="list" class="dragArea" :options="{group:'people'}">
            <div v-for="element in list">{{element.name}}</div>
        </draggable>

        <h2>List 2 Draggable</h2>
        <draggable v-model="list1" class="dragArea" :options="{group:'people'}">
            <!--<div v-for="element in list1">{{element.name}}</div>-->
            <div >Paul </div>
            <div > Ringo</div>
        </draggable>

        <h1> Draggable IMG's </h1>
        <draggable v-model="imgList" class="dragArea" :options="{group:'Items'}">
            <img :src="imgList[0].url">
            <img :src="imgList[1].url">
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
                    {url: require('../assets/1.png')},
                    {url: require('../assets/2.jpg')},
                ],
            }
        },

        methods:{
            fillImgArray(){
                var img = new Image();
                img.src = "http://yourimage.jpg";

                this.imgList[0].src = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" //splice(0, 1, )
            },
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
