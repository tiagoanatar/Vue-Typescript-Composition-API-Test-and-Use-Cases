<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>2 way data binding</h3>
      <p>{{twoWayDataBiding}}</p>
      <input v-model='twoWayDataBiding' />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'VmodelSample',
  setup() {
    const twoWayDataBiding = ref('2 way data binding')
    return { 
      twoWayDataBiding,
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
