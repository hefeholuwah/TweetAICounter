<template>
  <div id="app">
    <h1>Autobots Count: {{ autobotsCount }}</h1>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      autobotsCount: 0,
    };
  },
  created() {
    this.fetchAutobotsCount();
    setInterval(this.fetchAutobotsCount, 10000); // Fetch every 10 seconds
  },
  methods: {
    async fetchAutobotsCount() {
      const response = await axios.get(
        "https://tweetai.onrender.com/api/autobots/count"
      );
      this.autobotsCount = response.data.count;
    },
  },
};
</script>
