

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ data }}</h1>
    <button v-on:click="update">Reverse Message</button>

    <p></p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  props: {
    msg: String
  },

  data: () => ({
    data: null
  }),

  methods: {
    update: function() {
      this.data = this.data
        .split("")
        .reverse()
        .join("");
    }
  },

  mounted() {
    axios.get("/api").then(response => {
      this.data = response.data;
    });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
