<!-- Layouts -> how each page will loook-->

<template>
  <div>
    <AppHeader />
    <Nuxt />
  </div>
</template>

<script>
import AppHeader from '../components/AppHeader'
// console.log(AppHeader)

export default {
  components: {
    AppHeader,
  },
}
</script>
