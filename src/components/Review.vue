<template>
  <div class="review">
    <label> Name: {{ this.userName }}</label>
    <br />
    <label> Email: {{ this.userEmail }}</label>
    <br />
    <label> Todo: {{ this.todo }}</label>
  </div>
</template>


<script>
  export default {
    name: 'review',

    props: {
      userName: {
        type: String,
        required: true,
      },

      userEmail: {
        type: String,
        required: true,
      },

      todo: {
        type: String,
        required: true,
      }

    },
    data() {
      return {
      }
    },

    methods: {
    }
  }
</script>


<style scoped>

</style>