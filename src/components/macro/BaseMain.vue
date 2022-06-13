<template>
  <main class="pb-4">
      <ItemSection/>
  </main>
</template>

<script>
import ItemSection from '../sections/ItemSection.vue';

export default {
    name: 'BaseMain',
    components: {
        ItemSection,
    }
}
</script>

<style>

</style>