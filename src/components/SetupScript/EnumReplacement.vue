<template>
  <div>
    {{ msg }}
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';

// Enum replacement
withDefaults(defineProps
  <{
    msg?: 'uva' | 'pera'
    labels?: string[]
  }>
(), {})

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
