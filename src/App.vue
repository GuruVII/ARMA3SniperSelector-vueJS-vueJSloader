<template>
  <div id="app" class="container" v-on:addNameEvent="addNameEvent"><!--This listens for an $emit from a child -->
    <input-name></input-name>
    <names :names="names"></names>
  </div>
</template>

<script>
import Materialize from "materialize-css"
import InputName from './components/Input'
import Names from './components/Names'


export default {
  name: 'app',
  components: {
    InputName,
    Names
  },
  data () {
    return {
      names: ["Jure", "Janez", "Guru"]
    }
  },
  methods: {
    addNameEvent: function(){
      console.log("dela")
    }
  }
}
</script>

<style src="materialize-css/dist/css/materialize.min.css"></style>

