<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Emit function event sample</h3>
      <form>
        <ul>
          <RadioSample2 v-for="item in reactiveForLoop" @send-message="checkRadio" :key="item.id" :idItem="item.id" :value="item.name" :label="item.name" />
        </ul>
        {{ radioSelected }}
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, inject, reactive } from 'vue';
import RadioSample from '@/components/RadioEmit/RadioSample.vue'
import RadioSample2 from '@/components/RadioEmit/RadioSample2.vue'

export default defineComponent({
  name: 'RadioEmit',
  components: {
    RadioSample,
    RadioSample2
  },
  setup() {
    const reactiveForLoop = reactive([
      {id: 1, name: "John"},
      {id: 2, name: "Barbara"},
      {id: 3, name: "Don"},
      {id: 4, name: "Jack"}
    ])
    let radioSelected = reactive({
      title: "No",
      data: '',
      id: 0
    })
    function checkRadio(data: string, id: number){
      radioSelected.title = 'Yes';
      radioSelected.data = data;
      radioSelected.id = id;
    }
    return { 
      radioSelected,
      checkRadio,
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
