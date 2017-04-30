<template>
  <div class="row">
    <div class="col s6 offset-s3">
    <h5>Inputted names:</h5>
      <ul>
        <li v-for="name in names" >
        <p class="center-align">{{name}} <i class="tiny material-icons clear-icon" @click="deletePerson">clear</i></p></li>

      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'names',
  props: ["names"],
  methods:{
    deletePerson: function(index) {
     this.names.splice(index, 1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.clear-icon { 
  color: red;
  vertical-align: middle;
  line-height: 1.5; }
.clear-icon:hover {
  cursor: pointer;
}
.clear-icon:active {
  background: red;
}
</style>
