<template>
  <div class="kittens-index">
    <h1>All Kittens!</h1>
    <div v-for="kitten in kittens" v-bind:key="kitten.id">
      <p>Name: {{ kitten.name }}</p>
      <p>Age: {{ kitten.age }}</p>
      <p>Color: {{ kitten.color }}</p>
      <hr>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      kittens: []
    };
  },
  created: function() {
    this.indexKittens();
  },
  methods: {
    indexKittens: function() {
      axios.get("/kittens").then(response => {
        console.log(response.data);
        this.kittens = response.data;
      });
    },
  },
};
</script>
