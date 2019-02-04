<template>
  <div>
    <v-toolbar
        app
        fixed
        clipped-left
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>

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

    watch: {
      drawer: function ()
      {
        EventBus.$emit('boba', this.drawer)
      }

    }
  }

</script>

<style scoped>

</style>
