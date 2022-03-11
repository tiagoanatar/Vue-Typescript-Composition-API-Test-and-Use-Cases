<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Input ref sample</h3>
      <form>
        <ul>
          <Input />
        </ul>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, inject, reactive } from 'vue';
import Input from '@/components/RefHtmlElement/Input.vue'

export default defineComponent({
  name: 'RadioEmit',
  components: {
    Input,
  },
  setup() {
    const reactiveForLoop = reactive([
      {id: 1, name: "John"},
      {id: 2, name: "Barbara"},
      {id: 3, name: "Don"},
      {id: 4, name: "Jack"}
    ])
    return { 
      reactiveForLoop,
    }
  }
});
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
