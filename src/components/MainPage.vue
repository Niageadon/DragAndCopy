<template>
    <div>
        <v-container align-content-start>
            <h1>First component</h1>
            <v-switch pl-2
                      :label="`Enable `"
                      :color="'green'"
                      v-model="enablePut"
            ></v-switch>

            <h1>Second component</h1>
            <h2>List 1 Draggable</h2>
            <draggable v-model="list" class="dragArea" :options="{group:'Text'}">
                <div v-for="(element, Index) in list" :key="Index">{{element.name}} </div>
            </draggable>

            <h1> Draggable IMG's </h1>
            <draggable v-model="listItems" class="dragArea" :options="draggableOption('Images')">
                <img :src="listItems[0].src">
                <img :src="listItems[1].src">
            </draggable>
        </v-container>
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

                enablePut: true,
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
                        pull: false,
                        put: this.enablePut
                    },
                    animation: 400
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
        background-color: #ead2f1;
    }

    .box{
        height: 100px;
        width: 100px;
        background-image: url("../assets/1.png");
    }
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
