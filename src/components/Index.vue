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
    <div id="div-rectangle"></div>
  </div>
</template>

<script>
import axios from 'axios';
require('../assets/css/index.css');

export default {
  props: {
    msg: String,
  },
  methods: {
    request: async() => {
      const resp = await axios.get('https://jsonplaceholder.typicode.com/todos');
      const title = resp.data[0].title;
      const split = title.split(' ');

      for (let i = 0; i < split.length; i++) {
        const elem = document.getElementById('div-rectangle');
        const div = document.createElement("div");

        div.textContent = `${split[i]}`;
        div.className = `rectangle${i + 1}`;

        const anchor = document.createElement("a");
        anchor.textContent = `❌`;
        anchor.onclick = () => {
          const deleteNode = document.getElementsByClassName(`rectangle${i + 1}`);
          if (deleteNode.length > 0) deleteNode[0].remove();
        }
        div.appendChild(anchor);
        elem.appendChild(div);
      }
    }
  },
};
</script>
