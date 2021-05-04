<template>
  <div>
    <Nuxt-link to="/jokes">Back to Jokes</Nuxt-link>
    <h4>Welcome to parameterized specific jokes</h4>

    <small>Joke Id : {{ $route.params.id }}</small>
    <h2>{{ joke }}</h2>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      joke: {},
    }
  },

  async created() {
    const config = {
      headers: {
        Accept: 'application/json',
      },
    }

    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      )

      this.joke = res.data.joke

      console.log('The final Joke is', this.joke)
    } catch (error) {
      console.log(error)
    }
  },
  head() {
    return {
      title: this.joke,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'best place for jokes',
        },
      ],
    }
  },
}
</script>
