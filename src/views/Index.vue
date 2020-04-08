<template>
  <div id="Index" class="pageContainer">
    <div v-for="(item, index) in data" :key="index" @click="goToHomePage(item)">{{ item }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: ['首页1', '首页2', '首页3']
    }
  },
  methods: {
    goToHomePage(item) {
      localStorage.setItem('homeItem', item)
      this.$router.push('/Home')
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
