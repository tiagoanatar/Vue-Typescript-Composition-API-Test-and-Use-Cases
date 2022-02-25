<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Replace Enum with defaults props</h3>

    </div>
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
