<template>
  <header class="header">
    <h1 class="title">Dad jokes</h1>

    <h5>Test this</h5>

    <ul>
      <li>
        <nuxt-link to="/">Home</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/jokes">jokes</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/about">about</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
}
</script>

<style></style>
