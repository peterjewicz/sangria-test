<template>
  <div class="hello">
    <button v-on:click="this.sendRequest">Send Test Request</button>
  </div>
</template>

<script>
import ApolloClient from "apollo-boost";
import gql from "graphql-tag";
const axios = require('axios');

const client = new ApolloClient({
  uri: "http://localhost:8080/graphql"
});

export default {
  name: 'HelloWorld',
  data () {
    return {
    }
  },
  methods: {
    sendRequest() {
      // Here's an example just using Axios
      // axios({
      //   method: 'post',
      //   url: 'http://localhost:8080/graphql',
      //   data: {
      //     query: "{hero {friends {name}}}"
      //   }
      // }).then(response => {
      //   console.log(response)
      // });

      // And here we have an Apollo client example
      client
      .query({
        query: gql`
          {
            hero {friends {name}}
          }
        `
      }).then(result => console.log(result.data));

      // Example of making a request with arguments
      client
      .query({
        query: gql`
          {
            character(id: "1001") {name appearsIn friends {name}}
          }
        `
      }).then(result => console.log(result.data));
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
