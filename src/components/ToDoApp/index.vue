<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>To Do Form</h3>
      <form @submit.prevent="onSubmit">
        <InputSample type="text" v-model:valueRef="formState.name" placeholder="Task name" />
        <InputSample type="text" v-model:valueRef="formState.task" placeholder="Task description" />
        <input type="submit" value="Send" />
      </form>
      <h3>To Do List</h3>
      <ul>
        <ToDoItem v-for="item in todoList" :key="item.id" :data="item" />
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import InputSample from '@/components/FormEmitInputData/InputSample.vue'
import ToDoItem from '@/components/ToDoApp/ToDoItem.vue'

export default defineComponent({
  name: 'ToDoApp',
  components: {
    InputSample,
    ToDoItem
  },
  setup() {
    const todoList = reactive([
      { 
        id: 0,
        name: 'Build Town',
        task: 'Lorem ipsum dolor sec met isto.',
      },
      {
        id: 1,
        name: 'Cut Plants',
        task: 'Sec vani lux obinos mat nus.',
      },
    ]);
    let formState:any = reactive({
      id: 0,
      name: '',
      task: '',
    });
    function onSubmit(){
      const newTodo = {...formState}
      newTodo.id = todoList.length
      todoList.push(newTodo)
    };
    return { 
      todoList,
      formState,
      onSubmit
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
