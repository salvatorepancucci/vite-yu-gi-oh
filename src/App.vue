<script>
  import AppHeader from './components/AppHeader.vue'
  import AppMain from './components/AppMain.vue'

  export default {
    name: 'App',
    components: {
      AppHeader,
      AppMain
    }
  }
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss" scoped>
    @import '/src/components/styles/generals.scss';
</style>
