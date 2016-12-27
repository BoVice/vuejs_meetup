<template>
  <div id="app">
    <users :users="users" @createNewUser="handleNewUser" @createNewTodo="handleNewTodo" @deleteCurrentUser="handleDeleteUser" @updatedEmail="handleNewUserEmail" @updatedName="handleNewUserName" :disabled="isEnabled" :todo="todo" > </users>
    <review :userName="userName" :userEmail="userEmail" :todo="todo"></review>
  </div>
</template>

<script>
import Users from './components/users'
import Review from './components/review'

export default {
  name: 'app',
  components: {
    Users,
    Review,
  },

  data() {
      return {
        users: [
          {
            name: 'john doe',
            email: 'doe@gmail.com',
            contacted: false
          },

          {
            name: 'steve doe',
            email: 'steve@gmail.com',
            contacted: false
          },

           {
            name: 'tom doe',
            email: 'tome@gmail.com',
            contacted: false
          }
        ],
        userName: "",
        userEmail: "",
        disabled: false,
        todo: "",
      }
    },

  methods: {
    handleNewUser: function(user) {
        this.users.push({
          name: user.name,
          email: user.email,
          contacted: false,
        })
    },
    handleDeleteUser: function(user) {
      this.users.splice(this.users.indexOf(user), 1)
    },

    handleNewUserName: function(updatedName) {
      this.userName = updatedName
    },

    handleNewUserEmail: function(updatedEmail) {
      this.userEmail = updatedEmail
    },

    handleNewTodo: function(updatedTodo) {
      this.todo = updatedTodo
    }

  },

  computed: {
    isEnabled: function() {
      if (this.userName !== "" && this.userEmail != "" && this.todo != "") {
        return this.disabled = false
      }else{
        return this.disabled = true
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
