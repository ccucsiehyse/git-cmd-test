<!-- frontend/src/App.vue -->
<template>
  <div id="app">
    <h1>Random Number Generator</h1>
    <button @click="fetchRandomNumber">Generate Random Number</button>
    <p v-if="randomNumber !== null">Random Number: {{ randomNumber }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      randomNumber: null,
    };
  },
  methods: {
    async fetchRandomNumber() {
      try {
        const response = await axios.get('http://localhost:3000/random');
        this.randomNumber = response.data.random_number;
      } catch (error) {
        console.error('Error fetching random number:', error);
      }
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin-top: 50px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>

