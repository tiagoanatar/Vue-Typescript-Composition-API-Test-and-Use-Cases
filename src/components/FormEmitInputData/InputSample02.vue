<template>
    <input
      type="type"
      name="name"
      :placeholder="placeholder"
       @change='onChange'
    />
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'InputSample',
  props: {
    placeholder: {
      type: String,
      default: '',
    },
  },
  emits: ['send-data'],
  setup(props, context) {
    function onChange(e:Event){
      context.emit('send-data', e)
    } 
    return {
      onChange,
    }
  }
});
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
