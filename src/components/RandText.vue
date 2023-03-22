<template>
  <div>
    <h1 class="title">{{ title }}</h1>
    <p class="text">{{ text }}</p>
    <div class="null"></div>
    <button class="button" @click="fetchData">Generate Random Text</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      title: '',
      text: ''
    }
  },

  methods: {
    async fetchData() {
      const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
      const data = response.data[Math.floor(Math.random() * response.data.length)];

      this.title = data.title;
      this.text = data.body;
    }
  }
}
</script>


<style lang="scss">
.title {
  color: #00e2da;
  font-style: bold;
  font-size: 48px;
  font-weight: 800;
  max-width: 1080px;
  text-align: center;
  margin: 64px auto;
}

.text {
  font-style: italic;
  font-family: 'Times New Roman', Times, serif;
  font-weight: 600;
  font-size: 24px;
  color:azure;
  max-width: 1344px;
  margin: 48px auto;
}

.button {
  display: block;
  padding: 28px;
  font-size: 20px;
  margin: auto;
  text-align: center;
  border-radius: 64px;
  font-weight: 550;
  background-color:darkorchid;
}

.null {
  margin: 48px;
  padding: 16px;
}
</style>