<template>
  <div id="AdminLinkAdd">
    <h3>添加友链</h3>
    <el-form :model="form">
      <el-form-item label="名称">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="链接">
        <el-input v-model="form.src"></el-input>
      </el-form-item>
      <el-form-item label="图标链接">
        <el-input v-model="form.icon"></el-input>
      </el-form-item>
      <el-form-item label="描述">
        <el-input v-model="form.des"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button
          type="primary"
          @click="handleSubmit"
        >提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "AdminLinkAdd",
  data(){
    return {
      form: {
        src: "",
        name: "",
        icon: "",
        des: ""
      }
    }
  },
  methods: {
    async handleSubmit(){
      let {data} = await this.$axios({
        method: "post",
        url: "/admin/addLink",
        data: {
          src: this.form.src,
          icon: this.form.icon,
          name: this.form.name,
          des: this.form.des
        }
      })

      if (data.code !== 0)return

      this.$message.success("添加成功")
      this.$router.push("/link")

    }
  }
}
</script>

<style scoped>

</style>














