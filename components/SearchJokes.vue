<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="text" placeholder="Search jokes" />
    <input type="submit" value="Search Jokes" />
  </form>
</template>

<script>
export default {
  name: 'SearchJokes',

  data() {
    return {
      text: '',
    }
  },

  methods: {
    //  On submit, send the text entered to to parent Component
    //  with 'search-text' placeholder and this.text as a parameter
    onSubmit() {
      console.log('Inside on submit functions')
      this.$emit('search-text', this.text)
      this.text = ''
    },
  },
}
</script>

<style></style>
