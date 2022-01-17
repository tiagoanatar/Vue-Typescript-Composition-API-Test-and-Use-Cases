<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Component Loading</h3>
      <HelloWorld :msg="propsVBindTest"/>
      <h3>Dependency Injection Data</h3>
      <Child />
      * This avoid prop drilling  
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive, provide } from 'vue';
import HelloWorld from '@/components/DependencyInjection/HelloWorld.vue'
import Child from '@/components/DependencyInjection/Child.vue'

export default defineComponent({
  name: 'DependencyInjection',
  components: {
    HelloWorld,
    Child,
  },
  setup() {
    const data = reactive({level: 'Level text', message: 'Message text', id: '1'});
    provide('global', data);
    const propsVBindTest = ref('Prop v-bind test');
    return { 
      propsVBindTest,
      data,
    }
  }
});
</script>