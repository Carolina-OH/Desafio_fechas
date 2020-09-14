<template>
  <div id="app">
    <contador></contador>
  </div>
</template>

<script>
  import contador from "./contador.vue"
  export default {
    data() {
      return {
        message: 'Hola en vue',
      };
    },
    components:{contador},
  }
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: darkblue;
    background: lightblue;
  }
</style>