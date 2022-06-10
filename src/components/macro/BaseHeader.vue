<template>
  <header>
    <div class="container">
      <div class="row">
        <search-bar class="col-4"/>
      </div>
    </div>
  </header>
</template>

<script>
import SearchBar from '../commons/SearchBar.vue'

export default {
  name: 'BaseHeader',
  components: { 
    SearchBar 
  },
}

</script>

<style lang="scss">

</style>