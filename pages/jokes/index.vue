<template>
  <div>
    <h1>Jokes domain</h1>
    <!-- <Joke v-for="joke in jokes" v-bind:key=joke.id /> -->
    <Joke
      v-for="joke in jokes"
      :key="joke.id"
      :id="joke.id"
      :joke="joke.joke"
    />
  </div>
</template>

<script>
import axios from 'axios'
import Joke from '../../components/Joke'

export default {
  components: {
    Joke,
  },

  data() {
    return {
      jokes: [],
    }
  },

  async created() {
    const config = {
      headers: {
        Accept: 'application/json',
      },
    }

    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config)

      this.jokes = res.data.results

      console.log('The response that was received is', this.jokes)
    } catch (error) {
      console.log(error)
    }
  },

  head() {
    return {
      title: 'DAD JOKES',
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

<style></style>
