<template>
    <div>
        <v-container style="padding-top: 0">
            <v-switch pl-2
                      :label="`Enable Put`"
                      :color="'green'"
                      v-model="enablePut"
            ></v-switch>

            <v-container grid-list-md  class="container">
                <h2>Text area</h2>
                <v-layout align-start justify-center row fill-height>
                    <draggable v-model="listOfText" class="containerForItem" :options="getOption('Text')">
                        <v-flex v-for="(element, Index) in listOfText" :key="Index"
                                xs2
                        >
                            <v-card>
                                <v-card-title>
                                {{element.name}}
                                </v-card-title>
                            </v-card>
                        </v-flex>
                    </draggable>
                </v-layout>
            </v-container>

            <v-container grid-list-md class="container">
                <h2>Image area</h2>
                <v-layout align-start justify-center row fill-height>
                    <draggable v-model="listOfImages" class="containerForItem" :options="getOption('Images')">
                        <v-flex v-for="(element, Index) in listOfImages" :key="Index"
                                 xs2>
                            <v-card>
                                <v-img
                                    :src="element.src"

                                > </v-img>
                            </v-card>
                        </v-flex>
                    </draggable>
                </v-layout>
            </v-container>

            <v-container grid-list-md class="container">
                <h2>Image + Text area</h2>
                <v-layout align-start justify-center row fill-height>
                    <draggable v-model="listOfImagesAndText" class="containerForItem" :options="getOption('Text and Images')">
                        <v-flex v-for="(element, Index) in listOfImagesAndText" :key="Index"
                                xs2>
                            <v-card>
                                <v-img
                                    :src="element.src"
                                > </v-img>
                                <v-card-title> {{element.name}} </v-card-title>
                            </v-card>
                        </v-flex>
                    </draggable>
                </v-layout>
            </v-container>



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
                listOfText:[
                    {name:"HALA"},],

                listOfImages:[
                    {name: 'device 1', src: require('../assets/alphavite/space.png')},
                ],

                listOfImagesAndText:[
                    {name: 'some text', src: require('../assets/alphavite/space.png')},
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

            getOption(groupName){
                return{
                    group:{
                        name: groupName,
                        pull: false,         //отдача
                        put: this.enablePut  //приём
                    },
                    animation: 500,
                    sort: true
                }

            },
        },

        created(){
            //this.fillImgArray()
        },
        watch:{
            listOfImages(){
                for(let i = 0; i < this.listOfImages.length; i++){
                    //console.log(this.listOfImages[i].src === undefined)
                    //console.log(this.listOfImages[i].src)
                    if(this.listOfImages[i].src === undefined) {this.listOfImages.splice(i, 1)}
                }
            },
            listOfImagesAndText(){
                for(let i = 0; i < this.listOfImagesAndText.length; i++){
                    //console.log(this.listOfImages[i].src === undefined)
                    //console.log(this.listOfImages[i].src)
                    if(this.listOfImagesAndText[i].src === undefined) {this.listOfImagesAndText.splice(i, 1)}
                }
            },

            listOfText(){
                for(let i = 0; i < this.listOfText.length; i++){
                    //console.log(this.listOfImages[i].src === undefined)
                    //console.log(this.listOfImages[i].src)
                    if(!(this.listOfText[i].src === undefined)) {this.listOfText.splice(i, 1)}
                }
            }



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

    .container{
     padding-top: 0;
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

    .containerForItem{
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: flex-start;
        align-items: baseline;
        width: 100%;
    }
</style>
