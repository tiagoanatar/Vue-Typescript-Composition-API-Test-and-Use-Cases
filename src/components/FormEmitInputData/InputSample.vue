<template>
    <input
      type="type"
      :value="valueRef"
      :placeholder="placeholder"
      @input="$emit('update:valueRef', handleInputChange($event))"
    />
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'InputSample',
  props: {
    valueRef: {
      type: [ String, Number ],
      default: '',
    },
    placeholder: {
      type: String,
      default: '',
    },
  },
  setup() {
    const handleInputChange = (event: Event) => (event.target as HTMLInputElement).value
    return { handleInputChange }
  }
});
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
