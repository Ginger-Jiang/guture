<template>
  <div>
    <label v-if="label">{{ label }}</label>
    <slot />
    <span v-show="error">{{ error }}</span>
  </div>
</template>

<script>
/**
 * 职能
 * 1.校验
 * 2.label
 * 3.error
 */
import Schema from 'async-validator'
export default {
  inject: ['form'],
  props: {
    label: {
      type: String,
      default: ''
    },
    prop: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      error: ''
    }
  },
  mounted() {
    this.$on('validate', () => {
      this.validate()
    })
  },
  methods: {
    validate() {
      /**
       * 引入 sync-validate 插件
       * 获取校验规则与校验值
       */
      const value = this.form.model[this.prop]
      const rule = this.form.rules[this.prop]

      const schema = new Schema({ [this.prop]: rule })

      return schema.validate(
        { [this.prop]: value.trim() },
        errors => (this.error = errors ? errors[0].message : '')
      )
    }
  }
}
</script>