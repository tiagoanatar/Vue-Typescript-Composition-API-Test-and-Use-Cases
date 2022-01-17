<template>
    <li>{{ data.id }} - {{ data.name }} - {{ data.task }}</li>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'ToDoItem',
  props: {
    data: {
      type: Object,
      default: {}
    },
  },
});
</script>