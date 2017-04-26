<template>
  <div class="names row">
    <div class="col s6 offset-s3">
      <ul>
        <li v-for="name in names" class="center-align">
        {{name}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'names',
  props: ["names"]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
