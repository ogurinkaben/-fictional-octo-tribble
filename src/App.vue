<template>
  <div id="app">
    <Header />
    <AddUser v-on:add-user="addUser" />
  <Users v-bind:users="users" v-on:delete-user="deleteUser" />
  </div>
</template> 

<script>
import Users from './components/Users';
import AddUser from './components/AddUser';
import Header from './components/UI/Header';
import  axios from 'axios';
export default {
  name: 'app',
  components: {
   Users,
   Header,
   AddUser
  },
  data: function (){
    return {
      users: []
    }
  },
  methods: {
    deleteUser(id) {
      this.users = this.users.filter(user => user.id !== id);
        axios.delete(`https://jsonplaceholder.typicode.com/users/${id}`)
      .then(res => this.users = this.users.filter(user => user.id !== id))
      .catch(err => console.log(err))

    },
    addUser(newUser) {
      const {username, marked} = newUser;
      axios.post('https://jsonplaceholder.typicode.com/users', {
        username,
        marked
      })
      .then(res => this.users = [...this.users, res.data])
      .catch(err => console.log(err))
      this.users.push(newUser);
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/users?_limit=10')
    .then(res => this.users = res.data)
    .catch(err => console.log(err));

  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: monospace;
}

.btn {
  border:none;
}
</style>
