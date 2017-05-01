<template>
  <div class="row">
    
  
    <form class="col s12">
      <div class="row"> 
        <div class="input-field col s6 offset-s3">
          <input id="player_name" class="validate" placeholder="Input player name" type="text" v-model="inputName" autofocus @keyup.enter="addName" :disabled="!snipersNotSelected">
          <!-- forms with a single input behave strangely, mine reloaded if entered it and pressed enter -->
          <label for="player_name">Payer Name</label>
          <div class="input-field hidden-input">
            <input type="text">
          </div>
          <span class="error-test" v-if="inputName == ''">{{errorMsg}}</span>          
        </div>
      </div>    
    </form>
  
        
  </div>
</template>

<script>
export default {
  name: 'inputName',
  props: ["snipersNotSelected"],
  data () {
    return {
      inputName:"",
      errorMsg: "",
    }
  },
  methods:{
      addName: function(){
        if (this.inputName.trim() != ""){
          this.$emit("addNameEvent", this.inputName)
          this.inputName = ""
          this.errorMsg = ""
        }
        else {
          this.errorMsg = "Please enter a name"
        }
      },
      reset: function(){
        this.errorMsg = "";
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hidden-input{
  display: none;
}
.error-test{
  color: red;
  font-size: 0.7em;
}
</style>
