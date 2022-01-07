<template>
  <div class="home parent" v-cloak>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Conditional state style</h3>
        <p><img alt="Vue logo" src="../assets/logo.png" class="static" :class="{ activeClass: activeClass }"></p>
        <button @click="toggleClass" class="button-3">Click to Increase</button>
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Component Loading</h3>
        <HelloWorld :msg="propsVBindTest"/>
        <h3>Dependency Injection Data</h3>
        <DependencyInjection />
        * This avoid prop drilling  
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Counter</h3>
        <div class="counter">{{counter}}</div>
        <h3>Watch Counter</h3>
        <div class="counter">{{watchData}}</div>
        <p>* Increase every 4 counter clicks</p>
        <button @click="counterIncrease" class="button-3">Click to Increase</button>
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>2 way data binding</h3>
        <p>{{twoWayDataBiding}}</p>
        <input v-model='twoWayDataBiding' />
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>V-if and V-show</h3>
        <div v-if='vIfTest' class='box box1'>VIf Test Box</div>
        <div v-else-if='vIfTestA' class='box box2'>Else Box</div>
        <div v-show='vIfTest' class='box box3'>VShow Test Box</div>

        <button @click='toggleBox' class="button-3">Click to Show/Hide</button>
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>V-for sample with reactive</h3>
        <ul id="example-1">
          <li v-for="item in reactiveForLoop" :key="item.id">
            {{ item.name }}
          </li>
        </ul>
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Reactive Sample</h3>
        {{ reactiveData.title }}
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Prop sample and toRefs</h3>
        {{ propSampleA }} . {{ propSampleB }} . {{ propSampleC }}
      </div>
    </div>

    <div class="parent-child">
      <div class="parent-child-internal">
        <h3>Prop with typescript interface sample</h3>
        {{ propInterfaceSample.level }} . {{ propInterfaceSample.message }} . {{ propInterfaceSample.id }}
      </div>
    </div>

  </div>
</template>

<script lang="ts">
import { defineComponent, ref, toRefs, watch, reactive, onMounted, onUpdated, onUnmounted, PropType, provide } from 'vue'
import HelloWorld from '@/components/HelloWorld.vue'
import DependencyInjection from '@/components/DependencyInjection.vue'
import InterfaceSample from '@/types/InterfaceSample'

export default defineComponent({
  name: 'Home',
  components: {
    HelloWorld,
    DependencyInjection,
  },
  props: {
    propSampleA: {type: String, default: 'pro test A'},
    propSampleB: {type: String, default: 'pro test B'},
    propSampleC: {type: String, default: 'pro test C'},
    propInterfaceSample: {
      type: Object as PropType<InterfaceSample>, 
      default: {level: 'Level text', message: 'Message text', id: '1'},
      required: true
    },
  },
  setup(props, context) {

    // Conditional style
    const activeClass = ref(true)

    const toggleClass = ()=> {
      activeClass.value = !activeClass.value
    }

    // Ref + watch sample
    const counter = ref(1)

    const counterIncrease = ()=> {
      counter.value++
    }

    const watchData = ref(0)

    watch(counter, (count, prevCount) => {
      let test:number|any = count
      if (test % 4 === 0){
        watchData.value++
      }
    })

    // 2 way data binding
    const twoWayDataBiding = ref('2 way data binding')

    // Prop sample
    const propsVBindTest = ref('Prop v-bind test')

    // Reactive sample
    const reactiveData = reactive({
      title: "Hello, Vue 3"
    })

    // Reactive v-for sample
    const reactiveForLoop = reactive([
      {id: 1, name: "John Doe"},
      {id: 2, name: "Barbara Doe"},
      {id: 3, name: "Don Dinner"},
      {id: 4, name: "Jack Jackson"}
    ])

    // V-if sample
    const vIfTest = ref<boolean>(true)
    const vIfTestA = ref<boolean>(true)

    const toggleBox = ()=> {
      vIfTest.value = !vIfTest.value
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

    // Multiple values to ref
    const { propSampleA, propSampleB, propSampleC } = toRefs(props)

    // Props with interface sample
    const propInterfaceSample = reactive(props.propInterfaceSample)

    // Dependency injection
    provide('global', propInterfaceSample)

    return {
      activeClass,
      toggleClass,
      counter,
      watchData,
      twoWayDataBiding,
      vIfTest,
      vIfTestA,
      propsVBindTest, 
      toggleBox,
      counterIncrease,
      reactiveData,
      reactiveForLoop,
      propSampleA,
      propSampleB,
      propSampleC
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

.activeClass {
  filter: grayscale(100%);
}

.box {
  background-color: cornflowerblue;
  color: #fff;
  padding: 20px;
  border-radius: 20px;
  margin-bottom: 10px;
}

.box1 {
  background-color: cornflowerblue;
}

.box2 {
  background-color: black;
}

.box3 {
  background-color: orange;
}

[v-cloak] { /* this and the HTML will hide the application until everything is ready */
  display: none;
}

.parent {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-column-gap: 20px;
  grid-row-gap: 20px;
}

.parent .parent-child{
  background: #e0e0e0;
  transition: 0.5s;
  padding: 5px;
  background-color: #fff;
  -webkit-border-radius: 20px;
  -webkit-border-bottom-right-radius: 100px;
  -moz-border-radius: 20px;
  -moz-border-radius-bottomright: 100px;
  border-radius: 20px;
  border-bottom-right-radius: 100px;
  -webkit-box-shadow: 5px 5px 15px 5px rgba(0,0,0,0.5); 
  box-shadow: 5px 5px 15px 5px rgba(0,0,0,0.5);
}

.parent-child-internal {
  padding: 20px;
  color:#fff;
  background-color: #333;
  -webkit-border-radius: 20px;
  -webkit-border-bottom-right-radius: 100px;
  -moz-border-radius: 20px;
  -moz-border-radius-bottomright: 100px;
  border-radius: 20px;
  border-bottom-right-radius: 100px;
  min-height: 350px;
}

.parent .parent-child:hover{
  background-color: #1d8f3d;
  -webkit-border-radius: 20px;
  -webkit-border-bottom-right-radius: 20px;
  -moz-border-radius: 20px;
  -moz-border-radius-bottomright: 20px;
  border-radius: 20px;
  border-bottom-right-radius: 20px;
}

.counter {
  padding: 10px;
  color: white;
  background-color: #2ea44f;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  display: inline-block;
  margin-bottom: 10px;
}

.button-3 {
  appearance: none;
  background-color: #2ea44f;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}

.button-3:hover {
  background-color: #2c974b;
}

.button-3:disabled {
  background-color: #94d3a2;
  border-color: rgba(27, 31, 35, .1);
  color: rgba(255, 255, 255, .8);
  cursor: default;
}

.button-3:active {
  background-color: #298e46;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}

@media (max-width: 900px) {
  .parent-child-internal {
    min-height: 0px;
  }
  .parent {
    grid-template-columns: repeat(1, 1fr);
    grid-template-rows: repeat(1, 1fr);
}
}

</style>
