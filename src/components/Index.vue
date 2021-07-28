<template>
  <div id="app">
    <h1>{{ msg }}</h1>
    <p>
      Welcome to the website which call API with this link :
      https://jsonplaceholder.typicode.com/todos
    </p>
    <p>The main goal of this test is to get some accurate data.</p>
    <button v-on:click="request">
      Click to make request & get data
    </button>
    <div class="rectangle" v-for="(word, index) in words" :key="index">
      {{ word }}
      <a @click="deleteWord(index)">❌</a>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
require('../assets/css/index.css');

export default {
  props: {
    msg: String,
  },
  data() {
    return {
      words: []
    }
  },
  methods: {
    request() {
      axios.get('https://jsonplaceholder.typicode.com/todos')
			.then(
				response => this.words = response.data[0].title.split(' ')
			)
			.catch(error => console.log(error))
		},
    deleteWord(index) {
			this.words.splice(index, 1);
		}
  },
};
</script>
