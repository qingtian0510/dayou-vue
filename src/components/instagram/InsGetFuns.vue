<template>
  <div>
    <el-form ref="elForm" :model="formData" :rules="rules" size="medium" label-width="100px">
      <el-row type="flex" justify="start" align="middle">
        <el-form-item label="ins账号：" prop="field101">
          <el-input v-model="formData.field101" placeholder="请输入ins账号" clearable :style="{width: '100%'}">
          </el-input>
        </el-form-item>
        <el-col :span="10">
          <el-form-item label-width="0" prop="field104">
            <el-button type="primary" icon="el-icon-user" size="medium"> 采集 </el-button>
          </el-form-item>
        </el-col>
      </el-row>
      <el-form-item size="large">
        <el-button type="primary" @click="submitForm">提交</el-button>
        <el-button @click="resetForm">重置</el-button>
      </el-form-item>
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
        field101: undefined,
        field104: undefined
      },
      rules: {
        field101: [{
          required: true,
          message: '请输入ins账号',
          trigger: 'blur'
        }]
      }
    }
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {},
  methods: {
    submitForm () {
      this.$refs['elForm'].validate(valid => {
      })
    },
    resetForm () {
      this.$refs['elForm'].resetFields()
    }
  }
}

</script>
<style>
</style>
