<template>
  <div
    :class="cxRadio"
    @click="clickHandler"
  >
  <!--<div
    :class="isChecked.value ? 'form-check radio checked' : 'form-check radio'"
    @click="clickHandler"
  >-->
    <input
      :id="inputId"
      class="form-check-input"
      type="radio"
      :inputName="inputName"
      :value="value"
      :aria-describedby="describedBy"
      :disabled="disabled"
      :checked="isChecked.value"
    />
    <!-- eslint-disable-next-line vuejs-accessibility/label-has-for -->
    <label class="form-check-label" :for="inputId">
      {{ label }}
    </label>
  </div>
</template>

<script setup lang="ts">
import { reactive, watch, watchEffect, computed } from "vue";

// TODO: create data-automation id
interface Props {
  checkedValue?: string;
  describedBy?: string;
  disabled?: boolean;
  inputId?: string;
  inputName?: string;
  label: string;
  value: string;
}

const props = withDefaults(defineProps<Props>(), {
  checkedValue: "",
  describedBy: "Default describedby",
  disabled: false,
  inputId: "Default1D",
  inputName: "Default input name",
  hasOptional: "",
  label: "Default label",
});

const emit = defineEmits(["click"]);

const isChecked = reactive({ value: false });

function clickHandler() {
  emit("click", props.value);
  //console.log(isChecked.value);
}
~
/*
watch(
  () => props.checkedValue,
  (selection, old) => {
    if (selection === props.value) {
      isChecked.value = true;
    } else {
      isChecked.value = false;
    }
  }
);
*/


watchEffect(() => {
  if (props.checkedValue === props.value) {
    isChecked.value = true;
  } else {
    isChecked.value = false;
  }
})


const cxRadio = computed(() => [
  "form-check",
  "radio",
  isChecked.value && "checked",
]);
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  margin: 0;
  padding: 0;
}
ul li {
  list-style: none;
  border-bottom: 1px solid #000;
  padding: 10px;
}
</style>
