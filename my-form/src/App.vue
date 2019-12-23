<template>
  <div id="app">
    <Form></Form>
    <br />
    <!-- <Model /> -->
  </div>
</template>

<script>
import Form from '@/components/Form'
// import Model from '@/components/Vmodel'
export default {
  name: 'app',
  components: {
    Form
    // Model
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
