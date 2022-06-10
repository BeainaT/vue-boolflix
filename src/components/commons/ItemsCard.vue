<template>
  <ul class="item p-0 m-0 list-unstyled">
    <li>
      <h4>{{film.title}}</h4>
      <h4>{{film.original_title}}</h4>
      <h4>{{film.original_language}}</h4>
      <h4>{{film.vote_average}}</h4>
    </li>
  </ul>
</template>

<script>
export default {
    name: 'ItemCard',
    props: {
        film: Object,
    }
}
</script>

<style lang="scss" scoped>

</style>