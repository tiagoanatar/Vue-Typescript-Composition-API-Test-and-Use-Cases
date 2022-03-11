<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Counter</h3>
      <div class="counter">{{counter}}</div>
      <h3>Watch Counter</h3>
      <div class="counter">{{watchData}}</div>
      <p>* Increase every 4 counter clicks</p>
      <button @click="counterIncrease" class="button-3">Click to Increase</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch } from 'vue';

export default defineComponent({
  name: 'Counter',
  setup() {
    const counter = ref(1)
    const counterIncrease = ()=> {
      counter.value++
    }
    const watchData = ref(0)
    watch(counter, (count, prevCount) => {
      let test:number|any = count
      if (test % 4 === 0){
        watchData.value++
      }
    })
    return { 
      counter,
      counterIncrease,
      watchData
    }
  }
});
</script>