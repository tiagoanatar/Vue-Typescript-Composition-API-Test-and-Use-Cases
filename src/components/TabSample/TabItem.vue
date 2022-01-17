<template>
  <a 
    :class="position ? 'active' : '' " 
    @click="$emit('change-tab', item?.id)">
      {{ item?.label }}
  </a> <!-- '?' fix object unknown in typescript -->
</template>

<script lang="ts">
import { defineComponent, reactive, watch } from 'vue';

export default defineComponent({
  name: 'TabItem',
    props: {          
      item: {
        type: Object,
      },
      position: {
        type: Boolean,
      },
    },
  setup(props, context) {
    return { 
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  a {
    padding:10px;
    background-color:rgb(19, 7, 73);
    display: inline-block;
    cursor:pointer;
  }
  a.active {
    background-color: black;
  }
</style>
