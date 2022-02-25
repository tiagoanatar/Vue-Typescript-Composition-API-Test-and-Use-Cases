<template>
  <div @click="handleClick(msg)">
    {{ msg }}
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';

interface Props {
  msg?: string;
}

const props = withDefaults(defineProps<Props>(), {
  msg: 'test',
});

const emit = defineEmits(['send-message']);

function handleClick(msg:string) {
  emit('send-message', msg);
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
