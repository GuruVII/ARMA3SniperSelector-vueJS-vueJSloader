<template>
  <div class="input-name row">
    
  
    <form class="col s12">
      <div class="row"> 
        <div class="input-field col s6 offset-s3">
          <input id="player_name" type="text" v-model="inputName" autofocus @keyup.enter="addName">
          <!-- forms with a single input behave strangely, mine reloaded if entered it and pressed enter -->
          <input type="text" class="hidden-input">
          <label for="player_name">Player Name</label>
          <span class="error-test" v-if="inputName == ''">{{errorMsg}}</span>       
          <p>{{inputName}}</p>
          
        </div>
      </div>    
    </form>
  
        
  </div>
</template>

<script>
export default {
  name: 'input-name',
  data () {
    return {
      inputName:"",
      errorMsg: ""
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
