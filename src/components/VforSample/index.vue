<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>V-for sample with reactive</h3>
      <ul id="example-1">
        <li v-for="item in reactiveForLoop" :key="item.id">
          {{ item.name }}
        </li>
      </ul>
      <h3>V-for range</h3>
      <div id="range" class="demo">
        <span v-for="n in 10" :key="n">{{ n }} </span>
      </div>
      <h3>V-for from life cycle</h3>
      {{ feedArray }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue';

export default defineComponent({
  name: 'VforSample',
  props: {
    feedArray: {
      type: Array,
    }
  },
  setup() {
    const twoWayDataBiding = ref('2 way data binding');
    const reactiveForLoop = reactive([
      {id: 1, name: "John"},
      {id: 2, name: "Barbara"},
      {id: 3, name: "Don"},
      {id: 4, name: "Jack"}
    ]);
    return { 
      twoWayDataBiding,
      reactiveForLoop
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
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
