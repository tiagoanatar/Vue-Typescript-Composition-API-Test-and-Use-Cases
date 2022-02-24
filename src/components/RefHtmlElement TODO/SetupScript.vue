<template>
  <li>
    <label class="form-check-label" for="value">
      {{ msg }}
    </label>
  </li>
</template>

<script setup lang="ts">
import { reactive } from 'vue';

interface Props {
  msg?: string
  labels?: string[]
}

const props = withDefaults(defineProps<Props>(), {
  msg: 'hello',
  labels: () => ['one', 'two']
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
