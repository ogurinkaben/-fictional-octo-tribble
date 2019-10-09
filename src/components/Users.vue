<template>
  <div>
   
    <div v-bind:key="user.id" v-for="user in users">
       <User v-on:delete-user="$emit('delete-user', user.id)" v-bind:user="user" />
    </div>
  </div>
</template>

<script>
  import User from "./User.vue";
export default {
  name: 'Users',
  components: {
    User
  },
  props: ["users"]
  
}
</script>


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
