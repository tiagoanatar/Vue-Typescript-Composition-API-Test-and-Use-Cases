<template>
  <div class="parent-child">
    <div class="parent-child-internal">
      <h3>Tab Sample - Vfor + Vif</h3>
      <TabItem 
        v-for="item in data" 
        :item="item" 
        :key="item.id" 
        @change-tab="tabChange"
        :position="tabPosition.value === item.id ? true : false" 
      />
      <div v-for="item in data" :key="item.id">
        <div v-if="item.id == tabPosition.value" class="text">
          {{ item.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import TabItem from '@/components/TabSample/TabItem.vue';

interface Item {
  id: number;
  label: string;
  text: string;
}

export default defineComponent({
  name: 'TabSample',
  components: {
    TabItem,
  },
  setup() {
    const data = reactive<Item[]>([
      {
        id: 0,
        label: 'Item A',
        text: 'Lorem ipsun dolor met sic atanus severo lat. Fiat lux dominos act.'
      },
      {
        id: 1,
        label: 'Item B',
        text: 'Cosco deram suco itenet. Sominas et sic vart.'
      },
      {
        id: 2,
        label: 'Item C',
        text: 'Selerum acico danas, serem bastorada. Lorem, actus sine varse manto nas.'
      },
      {
        id: 4,
        label: 'Item D',
        text: 'As do selec tos nu bar faz sine varse manto nas.'
      },
    ]);
    const tabPosition = reactive({value: 0});
    function tabChange(id:number){
      tabPosition.value = id
    };
    return { 
      data,
      tabPosition,
      tabChange
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .text {
    border: 1px solid black;
    padding:20px;
  }
</style>
