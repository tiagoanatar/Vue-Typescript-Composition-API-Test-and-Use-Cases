<template>
  <div class="home parent" v-cloak>
    <FormEmitInputData />
    <RadioEmit />
    <ConditionalStyle />
    <DependencyInjection />
    <Counter />
    <VmodelSample />
    <VifVshow />
    <VforSample :feedArray="feedArray" />
    <Refs textA="test 01" textB="test 02" />
    <TabSample />
    <ToDoApp />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, onMounted, onUpdated, onUnmounted, PropType } from 'vue'

import FormEmitInputData from '@/components/FormEmitInputData/index.vue';
import RadioEmit from '@/components/RadioEmit/index.vue';
import ConditionalStyle from '@/components/ConditionalStyle/index.vue';
import DependencyInjection from '@/components/DependencyInjection/index.vue';
import Counter from '@/components/Counter/index.vue';
import VmodelSample from '@/components/VmodelSample/index.vue';
import VifVshow from '@/components/VifVshow/index.vue';
import VforSample from '@/components/VforSample/index.vue';
import Refs from '@/components/Refs/index.vue';
import TabSample from '@/components/TabSample/index.vue';
import ToDoApp from '@/components/ToDoApp/index.vue';

export default defineComponent({
  name: 'Home',
  components: {
    FormEmitInputData,
    RadioEmit,
    ConditionalStyle,
    DependencyInjection,
    Counter,
    VmodelSample,
    VifVshow,
    VforSample,
    Refs,
    TabSample,
    ToDoApp
  },
  props: {
    propSampleA: {type: String, default: 'pro test A'},
    propSampleB: {type: String, default: 'pro test B'},
    propSampleC: {type: String, default: 'pro test C'},
    propInterfaceSample: {
      type: Object as PropType<{level: string, message: string, id?: string
    }>, 
    default: {level: 'Level text', message: 'Message text', id: '1'},
    required: true
    },
  },
  setup(props, context) {

    const feedArray:number[] = reactive([])
    for(let i = 0 ; i < 10 ; i++){
      feedArray[i] = i
    }

    // Life cycle hooks
    onMounted(() => {
      console.log('mounted!')
    })
    onUpdated(() => {
      console.log('updated!')
    })
    onUnmounted(() => {
      console.log('unmounted!')
    })

    // Props with interface sample
    const propInterfaceSample = reactive(props.propInterfaceSample)

    return {
      feedArray
    }
  },
});
</script>

<style scoped>
ul {
  text-align: center;
  padding:0;
  margin:0;
}

li {
  border-bottom: 1px solid #999;
  display: block;
  padding:10px;
}

input {
	background-repeat: repeat;
	background-color: #FFF;
	color: #222;
	border-width: 1px;
	border-style: solid;
	border-color: #AAA;
	border-radius: 4px;
	box-shadow: 0 0 8px -3px #888;
  padding: 10px;
  display: inline-block;
  clear: both;
}

[v-cloak] { /* this and the HTML will hide the application until everything is ready */
  display: none;
}

</style>
