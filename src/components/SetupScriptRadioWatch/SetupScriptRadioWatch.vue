<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Radio Watch Sample</h3>

      <RadioWatch
          :checked-value="checkboxTest.value"
          value="This is the radio input data 1"
          input-name="input name 1"
          input-id="ex4m9l3-1d1"
          label="Example label"
          @click="clickEventRadio"
        />
      <RadioWatch
          :checked-value="checkboxTest.value"
          value="This is the radio input data 2"
          input-name="input name 2"
          input-id="ex4m9l3-1d2"
          label="Example label"
          @click="clickEventRadio"
        />
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import RadioWatch from './RadioWatch.vue'

const checkboxTest = reactive({value: ''})

function clickEventRadio(value: string) {
  checkboxTest.value = value;
  console.log(checkboxTest.value);
}

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
