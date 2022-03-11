<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>V-if and V-show</h3>
      <div v-if='vIfTest' class='box box1'>VIf Test Box</div>
      <div v-else-if='vIfTestA' class='box box2'>Else Box</div>
      <div v-show='vIfTest' class='box box3'>VShow Test Box</div>
      <button @click='toggleBox' class="button-3">Click to Show/Hide</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'VmodelSample',
  setup() {
    const vIfTest = ref<boolean>(true)
    const vIfTestA = ref<boolean>(true)
    const toggleBox = ()=> {
      vIfTest.value = !vIfTest.value
    }
    return { 
      vIfTest,
      vIfTestA,
      toggleBox
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
