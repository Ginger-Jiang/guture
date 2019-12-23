<template>
  <div>
    <!-- vmodel 语法糖本质 -->
    <input type="text" :value="value" @input="value = $event.target.value" />
    <p>绑定的值是{{ value }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: ''
    }
  }
}
</script>

<style lang="scss" scoped>
</style>