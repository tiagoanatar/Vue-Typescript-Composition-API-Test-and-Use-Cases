<template>
    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Conditional state style</h3>
        <p><img alt="Vue logo" src="@/assets/logo.png" class="static" :class="activeClass ? 'activeClass' : null"></p>
        <button @click="toggleClass" class="button-3">Change Style</button>
      </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'ConditionalStyle',
  setup() {
    const activeClass = ref(true)
    const toggleClass = ()=> {
      activeClass.value = !activeClass.value
    }
    return { 
      activeClass,
      toggleClass,
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .activeClass {
    filter: grayscale(100%);
  }

</style>
