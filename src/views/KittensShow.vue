<template>
  <div class="show-kitten">
    <p>Name: {{ kitten.name }}</p>
    <p>Age: {{ kitten.age }}</p>
    <p>Color: {{ kitten.color }}</p>
  </div>
</template>

<style></style>

<script>
import axios from 'axios'

  export default {
    data: function () {
      return {
        kitten: {},
      };
    },
    created: function () {
      axios.get(`/kittens/${this.$route.params.id}`).then(response => {
        console.log(response.data);
        this.kitten = response.data
      })
    },
    methods: {},
  };
</script>
