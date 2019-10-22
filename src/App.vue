<template>
  <div id="app">
    <Filters msg="Filters Test"/>
  </div>
</template>

<script>
import Filters from './components/Filters.vue'

export default {
  name: 'app',
  components: {
   Filters
  }
}
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
