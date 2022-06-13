<template>
  <header class="py-4">
    <div class="container">
      <div class="row justify-content-between">
        <LogoApp />
        <SearchBar class="col-4"/>
      </div>
    </div>
  </header>
</template>

<script>
import SearchBar from '../commons/SearchBar.vue';
import LogoApp from '../commons/LogoApp.vue';

export default {
  name: 'BaseHeader',
  components: { 
    SearchBar,
    LogoApp
  },
}

</script>

<style lang="scss">

</style>