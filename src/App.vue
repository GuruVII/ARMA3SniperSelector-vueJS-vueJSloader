<template>
  <div id="app" class="container"><!--This listens for an $emit from a child -->
    <loading-screen :currentlyLoadingProp="currentlyLoading" v-if="currentlyLoading" @loadingComplete="loadingComplete"></loading-screen>
    
    <input-name @addNameEvent="addNameEvent" :snipersNotSelected="snipersNotSelected" v-show="!currentlyLoading"></input-name>
    <transition name="fade">
      <sniper-selector :names="names" @snipersSelected="snipersSelected" v-show="!currentlyLoading"></sniper-selector>
    </transition>
    <names :names="names" v-if="snipersNotSelected"></names>
    <pro-tips></pro-tips>
    
  </div>
</template>

<script>
import Materialize from "materialize-css"
import InputName from './components/Input'
import Names from './components/Names'
import SniperSelector from './components/selectButton'
import LoadingScreen from './components/loadingScreen'
import ProTips from './components/proTips'


export default {
  name: 'app',
  components: {
    InputName,
    Names,
    SniperSelector,
    LoadingScreen,
    ProTips
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
    snipersSelected: function(value){
      this.snipersNotSelected = false;
      console.log("value: " + value);
      if (value > 0){ //do the loading screen only when more than 2 snipers were inputted
        this.currentlyLoading = true;
      }
      
    },
    loadingComplete: function(){
      this.currentlyLoading = false;
    }
  }
}
</script>

<style src="materialize-css/dist/css/materialize.min.css"></style>
<style scoped>
.fade-enter-active {
  transition: opacity .5s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0
}
.fade-leave-active,  {
  transition: opacity 0s
}
</style>

