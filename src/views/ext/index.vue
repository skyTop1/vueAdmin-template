<template>
  <div class="ext">
    <el-row :gutter="10">
      <el-col :span="12">
        <el-input type="text"
                  v-model="age"
                  @focus="setext" />
      </el-col>
      <el-col :span="12">
        <el-input type="text"
                  v-model="age"
                  @blur="setext" />
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
    },
    func() {
      console.log(typeof arguments === 'object')
      console.log(arguments[0])
      console.log(arguments[1])
      console.log(this)
    },
    enterSearchMember() {
      console.log('点击了enter')
    }
  },
  mounted() {
    this.setext()
    console.log(11)
  },
  created() {
    console.log('created')
    this.func(1, NaN)
    var that = this
    document.onkeydown = function(e) {
      var key = window.event.keyCode
      if (key === 13) {
        that.enterSearchMember()
      }
    }
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

