<script>
import AppHeader from './components/AppHeader.vue';
import AppFooter from './components/AppFooter.vue';



export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter,
  }
}

</script>

<template>
  <AppHeader />
  <router-view></router-view>
  <AppFooter />
</template>


<style lang="scss">
@use '../node_modules/bootstrap/scss/bootstrap.scss';
@use './style/general.scss' as*;
</style>
