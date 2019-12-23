<template>
  <div>
    <input type="text" :value="value" @input="onInput" />
  </div>
</template>

<script>
/**
 * 职能
 * 1.双向绑定
 * 2.触发校验
 */
export default {
  name: 'KInput',
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  methods: {
    onInput(e) {
      // v-model 监听 input
      this.$emit('input', e.taiget.value)
      // 触发校验 -> 父级自己派发 自己监听
      this.$parent.$emit('validate')
    }
  }
}
</script>