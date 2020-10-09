<template lang="pug">
  div(class="hello")
    h3 {{ msg }}
      ul
        li.list(v-for="list in Mass" :key="list.name")
          .left {{list.name}}
          .right {{' '+ list.time}}
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  data() {
    return {
      Mass: [],
      errors: [],
      msg: 'List',
    };
  },
  created() {
    const link = 'http://jsonplaceholder.typicode.com/users';

    axios.get(link)
      .then((response) => {
        this.Mass = response.data;
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li {
  margin-top: 20px;
}
.hello{
  width: 50%;
  margin: auto;
}
.list {
  display: flex;
  justify-content: space-between;
  border-left: 5px solid yellow;
  padding-left: 5px;
}
.left {
  display: flex;
}
.right {
  display: flex;
}
</style>
