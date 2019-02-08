<template>
  <div>
    <v-toolbar
        app
        fixed
        clipped-left
    >
      <v-toolbar-side-icon @click="bus"></v-toolbar-side-icon>

      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify + </span>
        <span class="font-weight-light">Vue.Draggable + Simplebar</span>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-radio-group style="max-width: 160px" v-model="styleTheme" row>
        <v-layout v-on:click="busTheme(styleTheme)" align-content-end>
        <v-radio  label="Light" value='light'></v-radio>
        <v-radio  label="Dark" value='dark'></v-radio>
        </v-layout>
      </v-radio-group>

    </v-toolbar>
  </div>
</template>

<script>
  import { EventBus } from '../../bus.js';

  export default {
    name: "ToolBar",

    data: function(){
      return{
        drawer: true,
        styleTheme: 'light',
        darkTheme: false // для шины
      }
    },

    methods:{
      bus(){ // управление положением боковой панели
        this.drawer = !this.drawer;
        EventBus.$emit('boba', this.drawer)
      },

      busTheme(colour){ // управление стилем приложения
        this.darkTheme = (colour === 'dark');
        EventBus.$emit('style', this.darkTheme);
      }

    },

    watch: {
    }
  }

</script>

<style scoped>

</style>
