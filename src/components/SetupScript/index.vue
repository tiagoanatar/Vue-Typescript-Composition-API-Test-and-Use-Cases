<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Replace Enum with defaults props</h3>
      <EnumReplacement msg="pera" />
      <hr />
      <h3>Setup script sample</h3>
      <SetupScriptSample msg="test" @send-message="showMessage" />
      {{ emitMessage.value }}
      <hr />
      <h3>Modal sample</h3>
      <Modal msg="test" @send-message="showMessage" />
      {{ emitMessage.value }}
      <hr />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import EnumReplacement from './EnumReplacement.vue'
import SetupScriptSample from './SetupScriptSample.vue'
import Modal from './Modal.vue'

export default defineComponent({
  name: 'RadioEmit',
  components: {
    EnumReplacement,
    SetupScriptSample,
    Modal
  },
  setup() {
    let emitMessage = reactive({
      value: "",
    })
    function showMessage(msg: string){
      emitMessage.value = msg + '1';
    }
    return { 
      emitMessage,
      showMessage,
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
