<template>
  <div>
    <el-form ref="elForm" :model="formData" :rules="rules" size="medium" label-width="100px">
      <el-row type="flex" justify="start" align="middle">
        <el-form-item label="ins账号：" prop="field101">
          <el-input v-model="formData.name" placeholder="请输入ins账号" clearable :style="{width: '100%'}">
          </el-input>
        </el-form-item>
        <el-form-item label="采集量：" prop="field101">
          <el-input v-model="formData.count" placeholder="请输入采集量" clearable :style="{width: '100%'}">
          </el-input>
        </el-form-item>
        <el-form-item size="large">
          <el-button type="primary" @click="submitForm">采集</el-button>
          <el-button @click="resetForm">重置</el-button>
        </el-form-item>
      </el-row>
    </el-form>
  </div>
</template>
<script>
export default {
  components: {},
  props: [],
  data () {
    return {
      formData: {
        name: 'qingtian423',
        count: 10
      }
      // rules: {
      //   field101: [{
      //     required: true,
      //     message: '请输入ins账号',
      //     trigger: 'blur'
      //   }]
      // }
    }
  },
  methods: {
    submitForm () {
      this.$refs['elForm'].validate(valid => {
        // TODO 提交表单
      })
      console.log(`name: ${this.formData['name']} , count: ${this.formData['count']}`)
      this.$axios
        .get('/ins/funs', {
          params: {
            name: this.formData.name,
            count: this.formData.count
          },
          dataType: 'jsonp',
          crossDomain: true
        })
        .then(successResponse => {
          console.log(successResponse)
          if (successResponse.data.code === 200) {
            // var data = this.loginForm
            var path = this.$route.query.redirect
            this.$router.replace({path: path === '/' || path === undefined ? '/index' : path})
          }
        })
        .catch(failResponse => {
        })
    },
    resetForm () {
      this.$refs['elForm'].resetFields()
    }
  },
  mounted () {
    console.log(`The initial count is ${this.formData['count']}.`)
  }
}

</script>
<style>
</style>
