<template>
  <li @click="$emit('send-message', value, idItem)" style="display:block;">
    <input
      class="form-check-input"
      type="radio"
      name="value"
      :value="value"
      id="value"
      :checked="idSelected === idItem"
    />
    <label class="form-check-label" for="value">
      {{ label }}
    </label>
  </li>
</template>

<!-- TODO: complete composition API implementation -->
<script lang="ts">
import { defineComponent, reactive, watchEffect, watch } from 'vue';

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
    idItem: {
      type: Number,
      default: null,
    },
    idSelected: {
      type: Number,
      default: null,
    },
    checked: {
      type: Boolean,
      default: false,
    }
  },
  setup(props){

    // Sample without use on this component logic
    watchEffect(() => {
        if(props.idItem === props.idSelected){
          //
        } else {
          //
        }
        console.log(props.idSelected) // => input
      }
    )

    return {
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
