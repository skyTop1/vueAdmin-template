<template>
  <div class="ext">

  </div>
</template>
<script>
export default {
  name: 'ext',
  data() {
    return {}
  },
  modules: {
    setext() {
      const o = {}
      console.log(o)
    }
  },
  methods() {
    this.setext()
  }
}
</script>
<style lang="scss" scoped>
.ext {
  height: 100%;
  background-color: #ccc;
}
</style>

