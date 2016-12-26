<template>
  <div class="users">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter name" @input="$emit('updatedName', newUser.name)">
      <br />
      <input type="text" v-model="newUser.email" placeholder="Enter email" @input="$emit('updatedEmail', newUser.email)" >
      <br />
      <input type="submit" value="Submit" >
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted: user.contacted}">
          {{user.name}}: {{user.email}} <button v-on:click="deleteUser(user)">x</button>
        </span>
      </li>
    </ul>
  </div>
</template>


<script>
  export default {
    name: 'users',

    props: {
      users: {
        type: Array,
        required: true,
      },
    },
    data() {
      return {
        newUser: {},
      }
    },

    methods: {
      addUser: function(e) {
        e.preventDefault();
        this.$emit("createNewUser", this.newUser)
        this.newUser.name = ""
        this.newUser.email = ""
      },
      deleteUser: function(user) {
        this.$emit("deleteCurrentUser", user)
      },
    }
  }
</script>


<style scoped>
  .contacted {
    text-decoration: line-through;
  }
</style>