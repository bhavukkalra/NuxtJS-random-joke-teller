<!--This component will be rendered for each joke that is received  -->
<template>
  <!-- :to used for dynamic linking with export default(to for simple) -->

  <Nuxt-link :to="'jokes/' + id">
    <div class="joke">
      <h2>Sample Text here for testing something</h2>
      <p>{{ joke }}</p>
    </div>
  </Nuxt-link>

  <!-- <div class="joke">
    <h2>Sample Text here for testing something</h2>
    <p>{{ joke }}</p>
  </div> -->
</template>

<script>
export default {
  name: 'Joke',
  props: ['joke', 'id'],
}
</script>

<style>
.joke {
  padding: 1rem;
  border: 1px solid #ccc;
  margin: 1rem 0;
}
</style>
