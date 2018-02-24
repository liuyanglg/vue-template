<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <el-button @click="say()">点击弹窗</el-button>
  </div>
</template>

<script>
import axios from 'axios'
import qs from 'qs'

const http=axios.create({
  baseURL:"http://localhost:8822/",
  headers:{
    'Content-Type':'application/json;charset=utf-8',
    'Access-Control-Allow-Origin':'*',
    "Access-Control-Allow-Headers": "Content-Type,Content-Length, Authorization, Accept,X-Requested-With",
    "Access-Control-Allow-Methods":"PUT,POST,GET,DELETE,OPTIONS"
  },
  proxy:{
    host:'127.0.0.1',
    port:8822
  }
});

export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    say: function () {
      console.log('Hello ' + this.name + '!');
      http.get('/v1/cards/J9PDTJ')
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
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
