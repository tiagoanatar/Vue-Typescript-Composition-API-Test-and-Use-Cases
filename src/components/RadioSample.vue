<template>
    <label class="form-check-label" for="value">
    <input
      class="form-check-input"
      type="radio"
      name="value"
      :value="value"
      id="value"
      @change="$emit('send-message', true)"
    />
      {{ label }}
    </label>
</template>

<!-- TODO: complete composition API implementation -->
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'RadioSample',
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
  },
  setup(){
    
    return {}
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form-check-label {
  display:block;
  padding:10px;
  background-color: gray;
}

.form-check-label.active {
  background-color: turquoise;
}
</style>
