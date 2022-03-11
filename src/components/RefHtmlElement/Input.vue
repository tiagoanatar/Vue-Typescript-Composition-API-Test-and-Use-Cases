<template>
    <input type="text" ref="input" @change="onChange" />
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue';

interface Props {
  msg?: string
  labels?: string[]
}

const props = withDefaults(defineProps<Props>(), {
  msg: 'hello',
  labels: () => ['one', 'two']
})

const input = ref()

function onChange(){
  console.log(input.value.value)
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
