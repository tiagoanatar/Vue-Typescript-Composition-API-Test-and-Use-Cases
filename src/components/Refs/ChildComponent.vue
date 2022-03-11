<template>
  <h3>Parent to Child</h3>
  {{ propSampleA }}
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ChildComponent',
  props: {
    propSampleA: {type: Number},
  },
  setup() {
    return { 
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
</style>