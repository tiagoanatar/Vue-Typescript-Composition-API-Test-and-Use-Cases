<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Computed Sample</h3>
      Made to manipulate multiple props/data in a function
      {{ classIconName }}<br />
      {{ props.msg }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, computed } from 'vue';

interface Props {
  msg?: string;
}

const props = withDefaults(defineProps<Props>(), {
  msg: 'test',
});

const classIconName = computed<string>(() => `theme-icon-${props.msg}`);

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
