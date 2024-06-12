<script>
  import AppHeader from './components/AppHeader.vue'
  import AppMain from './components/AppMain.vue'
  export default {
    data() {
      return {

      }
    },
    components: {
      AppHeader,
      AppMain
    }
  }
</script>

<template>
  <AppHeader/>
  <AppMain/>
</template>

<style lang="scss">
  @use './style/general.scss';
  @use './style/partials/mixins' as *;
  @use './style/partials/variabili' as *;
  @use '../node_modules/bootstrap/scss/bootstrap.scss';
</style>