<template>
  <li @click="$emit('send-message', value, idItem)" style="display:block;">
    <input
      class="form-check-input"
      type="radio"
      name="value"
      :value="value"
      id="value"
      ref="test"
      :checked="idSelected === idItem"
    />
    <label class="form-check-label" for="value">
      {{ label }}
    </label>
  </li>
</template>

<script setup lang="ts">
import { defineComponent, ref, reactive, watchEffect, watch } from 'vue';

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
    const checkedValue = reactive({value: false})
    const test = ref(null as unknown as HTMLInputElement)

    watchEffect(() => {
        if(props.idItem === props.idSelected && test.value){
          //test.value.checked = true
          checkedValue.value = true
        } else {
          //test.value.checked = false
          checkedValue.value = false
        }
        console.log(props.idSelected) // => input
      }
    )

    return {
      checkedValue,
      test
    }
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
