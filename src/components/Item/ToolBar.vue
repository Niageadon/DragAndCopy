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

      <v-btn
          flat
          href="https://github.com/vuetifyjs/vuetify/releases/latest"
          target="_blank"
      >
        <span class="mr-2">Latest Release</span>
      </v-btn>
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
      }
    },

    methods:{
      bus(){
        this.drawer = !this.drawer;
        EventBus.$emit('boba', this.drawer)
      }

    },

    watch: {
      drawer: function ()
      {
      }

    }
  }

</script>

<style scoped>

</style>
