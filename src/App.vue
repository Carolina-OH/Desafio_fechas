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

  }
</style>