<template>
  <div>
    <h1>Jokes domain</h1>
    <!-- We are emiting an event called search-text from children component-->
    <!-- When it is received Invoke a Method searchText -->
    <SearchJokes v-on:search-text="searchText" />

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
import SearchJokes from '../../components/SearchJokes'

export default {
  components: {
    Joke,
    SearchJokes,
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

      //   console.log('The response that was received is', this.jokes)
    } catch (error) {
      console.log(error)
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: 'application/json',
        },
      }

      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config
        )
        this.jokes = res.data.results
        // console.log('The text received is', text)
        // console.log('The data received is', res.data.results)

        // console.log('The response that was received is', this.jokes)
      } catch (error) {
        console.log(error)
      }
    },
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
