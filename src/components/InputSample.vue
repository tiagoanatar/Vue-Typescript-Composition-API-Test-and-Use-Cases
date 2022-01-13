<template>
    <input
      type="text"
      :value="value"
      :placeholder="placeholder"
      @input="$emit('update:value', $event.target.value)"
    />
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'InputSample',
  props: {
    value: {
      type: [ String, Number ],
      default: '',
    },
    placeholder: {
      type: String,
      default: '',
    },
  },
  setup() {
  }
});
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
