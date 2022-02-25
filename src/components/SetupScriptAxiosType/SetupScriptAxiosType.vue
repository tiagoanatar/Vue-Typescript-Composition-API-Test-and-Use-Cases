<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Axios Response Type</h3>
      {{ data.value[3] }}
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from 'axios'
import { reactive } from 'vue';

const data = reactive({value: []})

axios.get('https://jsonplaceholder.typicode.com/posts')
  .then(function (response) {
    data.value = response.data;
    console.log(data.value);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
  .then(function () {
    // always executed
  });

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  ul {
    margin: 0;
    padding: 0;
  }
  ul li {
    list-style: none;
    border-bottom: 1px solid #000;
    padding: 10px;
  }
</style>
