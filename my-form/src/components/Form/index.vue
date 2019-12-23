<template>
  <div>
    <KFrom ref="form" :model="model" :rules="rules">
      <KFormitem lable="用户名" prop="uname">
        <KInput v-model="model.uname"></KInput>
      </KFormitem>
      <KFormitem lable="密码" prop="pwd">
        <KInput v-model="model.pwd"></KInput>
      </KFormitem>
      <KFormitem>
        <button @click="submit">校验</button>
      </KFormitem>
    </KFrom>
  </div>
</template>

<script>
import KFrom from './KForm'
import KFormitem from './KFormitem'
import KInput from './KInput'
export default {
  components: { KFrom, KFormitem, KInput },
  data() {
    return {
      model: {
        uname: '',
        pwd: ''
      },
      rules: {
        uname: [{ required: true, message: '用户名不能为空' }],
        pwd: [{ required: true, message: '密码不能为空' }]
      }
    }
  },
  methods: {
    submit() {
      this.$refs.form.validate(isValidate => {
        if (isValidate) {
          alert('校验通过')
        } else {
          alert('校验失败')
        }
      })
    }
  }
}
</script>

<style scoped>
</style>