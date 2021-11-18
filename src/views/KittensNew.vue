<template>
  <div class="kittens-new">
    <h1>Create a Kitten!</h1>
    <form v-on:submit.prevent="createKitten()">
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <p>Name: <input type="text" v-model="newKitten.name" /></p>
      <p>Age: <input type="text" v-model="newKitten.age" /></p>
      <p>Color: <input type="text" v-model="newKitten.color" /></p>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      newKitten: {},
      errors: [],
    };
  },
  created: function() {
  },
  methods: {
    createKitten: function() {
      axios.post("/kittens", this.newKitten).then(response => {
        console.log(response.data);
        this.newKitten = {};
        this.$router.push("/kittens");
      }).catch((error) => {
        console.log(error.response);
        this.errors = error.response.data.errors;
      });
    },
  },
};
</script>