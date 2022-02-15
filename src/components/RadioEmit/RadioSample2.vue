<template>
  <li>
    <label class="form-check-label" for="value">
    <input
      class="form-check-input"
      type="radio"
      name="value"
      :value="value"
      id="value"
      @change="onChange(value, idItem)"
    />
      {{ label }}
    </label>
  </li>
</template>

<!-- TODO: complete composition API implementation -->
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'RadioSample2',
  props: {
    label: {
      type: String,
      default: 'Default label',
    },
    value: {
      type: [String, Number],
      default: '',
    },
    idFor: {
      type: String,
      default: '',
    },
    idItem: {
      type: Number,
      default: null,
    }
  },
  setup(props, context){
    function onChange(value: any, idItem: any) {
      context.emit('send-message', value, idItem);
    }
    return {
      onChange
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
