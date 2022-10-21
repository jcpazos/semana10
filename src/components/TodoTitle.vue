<template>
    <img alt="TODOs logo" src="../assets/todos-icon.png">
    <h1 class="display-1">{{ msg }}</h1>
</template>

<script>
export default {
  name: 'TodoTitle',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
