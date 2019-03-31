<template>
  <div class="hello">
    <button v-on:click="this.sendRequest">Send Test Request</button>
  </div>
</template>

<script>

const axios = require('axios');

export default {
  name: 'HelloWorld',
  data () {
    return {
    }
  },
  methods: {
    sendRequest() {
      axios({
        method: 'post',
        url: 'http://localhost:8080/graphql',
        data: {
          query: "{hero {friends {name}}}"
        }
      }).then(response => {
        console.log(response)
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
