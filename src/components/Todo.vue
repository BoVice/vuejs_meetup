<template>
  <div class="todo">
    <br />
      <input type="text"placeholder="Enter item" @input="$emit('updatedTodo', todo)" v-model="todo">
    <br />
  </div>
</template>


<script>
  export default {
    name: 'todo',

    props: {
    },
    data() {
      return {
        todo: ""
      }
    },

    methods: {
    }
  }
</script>


<style scoped>

</style>