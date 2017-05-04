<template>
  <div id="app" class="container"><!--This listens for an $emit from a child -->
    <loading-screen :currentlyLoadingProp="currentlyLoading" v-if="currentlyLoading" @loadingComplete="loadingComplete"></loading-screen>
    <input-name @addNameEvent="addNameEvent" :snipersNotSelected="snipersNotSelected" v-show="!currentlyLoading"></input-name> 
    <sniper-selector :names="names" @snipersSelected="snipersSelected" v-show="!currentlyLoading"></sniper-selector>
    <names :names="names" v-if="snipersNotSelected"></names>
  </div>
</template>

<script>
import Materialize from "materialize-css"
import InputName from './components/Input'
import Names from './components/Names'
import SniperSelector from './components/selectButton'
import LoadingScreen from './components/loadingScreen'


export default {
  name: 'app',
  components: {
    InputName,
    Names,
    SniperSelector,
    LoadingScreen
  },
  data () {
    return {
      names: [],
      snipersNotSelected: true,
      currentlyLoading: false
    }
  },
  methods: {
    addNameEvent: function(name){
      this.names.push(name)
    },
    snipersSelected: function(){
      this.snipersNotSelected = false;
      this.currentlyLoading = true;
    },
    loadingComplete: function(){
      this.currentlyLoading = false;
    }
  }
}
</script>

<style src="materialize-css/dist/css/materialize.min.css"></style>

