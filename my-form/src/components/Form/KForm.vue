<template>
  <div>
    <slot />
  </div>
</template>

<script>
/**
 * 职能
 * 1.数据持有丶传递
 * 2.全局校验
 */
export default {
  props: {
    model: {
      type: Object
    },
    rules: {
      type: Object
    }
  },
  provide() {
    return {
      form: this
    }
  },
  methods: {
    validate(cb) {
      /**
       * 全局校验
       * 获取所有子组件
       * 找到带有prop验证的
       * 调用子组件自身的校验方法
       */
      const tasks = this.$children
        .filter(item => item.prop)
        .map(item => item.validate())

      Promise.all(tasks)
        .then(() => cb(true))
        .catch(() => cb(false))
    }
  }
}
</script>

<style scoped>
</style>