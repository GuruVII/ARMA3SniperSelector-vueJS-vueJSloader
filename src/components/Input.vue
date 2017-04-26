<template>
  <div class="input-name row">
    
  
    <form class="col s12">
      <div class="row"> 
        <div class="input-field col s6 offset-s3">
          <input id="player_name" type="text" class="validate">
          <label for="player_name">Player Name</label>
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
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
