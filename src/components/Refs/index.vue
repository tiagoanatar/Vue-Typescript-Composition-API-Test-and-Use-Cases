<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Prop sample</h3>
      {{ textA }} . {{ textB }}
      <h3>Refs</h3>
      {{ propSampleA }} . {{ propSampleB }}
      <h3></h3>
      <ChildComponent :propSampleA="propSampleA" /><br/>
      <button @click="counterIncrease" class="button-3">Click to Increase</button><br /><br />
      <input type="text" placeholder="nothing" ref="inputRef" /> 
      {{ inputRef }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import ChildComponent from '@/components/Refs/ChildComponent.vue';

export default defineComponent({
  name: 'Refs',
  components: {
    ChildComponent
  },
  props: {
    textA: {type: String, default: 'pro test A'},
    textB: {type: String, default: 'pro test B'},
  },
  setup() {
    const propSampleA = ref(1);
    const propSampleB = ref(1);
    const inputRef = ref('')
    const counterIncrease = ()=> {
      propSampleA.value++
    };
    return { 
      propSampleA,
      propSampleB,
      counterIncrease,
      inputRef
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
