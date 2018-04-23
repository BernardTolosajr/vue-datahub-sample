<template>
  <div>
    <ul>
      <li v-for="user in users" v-bind:key="user.id">
        {{ user.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import 'whatwg-fetch';

export default {
  name: 'HelloWorld',
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    fetch('/api/users').then((response) => {
      return response.json();
    }).then((data) => {
      this.users = data.data;
    });
  },
};
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
