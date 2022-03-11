<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Child inputs - v-model</h3>
      <InputSample type="text" v-model:valueRef="formData.name" placeholder="Type Your Name" />
      <InputSample type="email" v-model:valueRef="formData.email" placeholder="Type Your Email" />
      <h3>Parent object fed by emit</h3>
      {{ formData }}
      <h3>Child inputs - custom event</h3>
      <form @submit.prevent="onSubmit">
        <InputSample02 type="text" name="name" placeholder="Type Your Name" @send-data="formChange" />
        <InputSample02 type="email" name="email" placeholder="Type Your Email" @send-data="formChange" />
        <input type="submit" value="Send" />
        <h3>Parent object fed by emit</h3>
        {{ formData02 }}
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, inject, reactive } from 'vue';
import InputSample from '@/components/FormEmitInputData/InputSample.vue'
import InputSample02 from '@/components/FormEmitInputData/InputSample02.vue'

export default defineComponent({
  name: 'FormEmitInputData',
  components: {
    InputSample,
    InputSample02,
  },
  setup() {
    const formData = reactive({
      name: 'Tiago Tavares',
      email: 'email@email.com',
    });
    let formData02:any = reactive({
      name: '',
      email: '',
    });
    function formChange(e:Event):void{
      let name = (e.target as HTMLInputElement).name;
      formData02[name] = (e.target as HTMLInputElement).value;
    };
    function onSubmit(){
      console.log(formData02)
    }
    return { 
      formData,
      formData02,
      formChange,
      onSubmit
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
