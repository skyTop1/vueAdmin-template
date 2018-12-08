<template>
  <div class="ext">
    <el-row :gutter="10">
      <el-col :span="12">
        <el-input type="text" v-model="age" @focus="setext"/>
      </el-col>
      <el-col :span="12">
        <el-input type="text" v-model="age" @blur="setext"/>
        </el-col>
    </el-row>
  </div>
</template>
<script>
export default {
  name: 'ext',
  data() {
    return {
      age: 1
    }
  },
  methods: {
    setext() {
      const o = {}
      console.log(o)
      console.log(this.age)
    }
  },
  mounted() {
    this.setext()
    console.log(11)
  },
  created() {
    console.log('created')
  }
}
</script>
<style lang="scss" scoped>
.ext {
  height: 100%;
  background-color: #ccc;
  min-height: 500px;
  padding: 10px;
}
</style>

