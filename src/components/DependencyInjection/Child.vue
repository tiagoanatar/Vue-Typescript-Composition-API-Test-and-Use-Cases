<template>
  <div class="box bo3">
    {{ globalData.message }}
  </div>
</template>

<script lang="ts">
import { defineComponent, inject, onMounted } from 'vue';

export default defineComponent({
  name: 'Child',
  setup() {
    interface Test {level: String; message: String; id: String}
    const globalData:any = inject('global')

    onMounted(() => {
      console.log(globalData)
    })

    return { globalData }
  }
});
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
