<template>
  <div class="row">
    <div class="col s12  center-align">
      <a class="waves-effect waves-light btn" :class="{disabled:((this.names.length < 2) || snipersSelected )}" @click="selectSnipers()">Select Snipers</a>
    </div>
    <div class="col s6 offset-s3 margin-top-20px" v-if="snipersSelected && !annoyed">
    <h5>The snipers are:</h5>
      <ul>
        <li v-for="name in selectedSnipers" class="center-align">
        <p :class="{ hella:(name.toLowerCase().includes('hel'))}">{{name}} <i class="tiny material-icons sniper-icon">done</i></p></li>
      </ul>
    </div>
    <div class="col s8 offset-s2 center-align">
      <p v-if="annoyed">I won't even dignify this with a response. Or you know what, the snipers are Hella and Sorter</p>
    </div>


  </div>
</template>

<script>
export default {
  name: 'sniperSelector',
  data(){
    return{
      snipersSelected: false,
      selectedSnipers: [],
      annoyed: false,
      currentlyLoading: false
    }
  },
  props: ["names"],
  methods:{
    selectSnipers: function(){
      // checks if only two snipers were selected
      if (this.names.length == 2){
        this.annoyed = true       
      }
      //selects the snipers from the inputted snipers
      for (var i = 0; i < 2; i++){
        var winner = Math.floor(Math.random() * (this.names.length - 1))
       this.selectedSnipers.push(this.names[winner]);
       this.names.splice(winner, 1);
      }
      this.snipersSelected = true;
      this.$emit("snipersSelected", this.names.length);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.margin-top-20px{
  margin-top: 20px;
}
.sniper-icon{
  color: green;
  line-height: 1.5
}
.hella {
  color: #F0A8C0;
}
</style>
