<template>
  <div id="app">
    <!-- 组件的静态传值 -->
    <Static message = "i am static meassage"></Static>
    <div>App组件内部倒计时60s:{{timeNum}}</div>
    <!-- 组件的动态传值 -->
    <Dynamic :message = "timeNum" :obj = "obj" :arr = "arr" v-bind = "obj"></Dynamic>
    <!-- 属性不绑定v-bind，直接传递的话，prop永远是string类型 -->
    <PropValidator :propA = "propString" :propC = 1></PropValidator>
    <NoPropsAttribute data-date-picker="activated" class="form-control" style="background: red"></NoPropsAttribute>
    <hr>
    <!-- v-on监听自定义change事件 -->
    <EventComp v-on:change="onChange" v-bind:value="timeNum"></EventComp>
    {{message}}
    <!-- 组件和数据的双向绑定 -->
    <!-- v-model语法糖，实际是v-bind:value="message" v-on:input="message=$event.target.value"-->
    <EventCompM v-model="message"></EventCompM>
    <!-- v-on的native修饰符会把原生事件focus直接添加到该组件的根元素上，如果根元素不是input表单元素，那么会静默监听失败，不会报错，但是onFocus也不会如期的被调用。 -->
    <EventCompL v-on:focus.native="onFocus"></EventCompL>
    <!-- $listeners专门为解决这个问题而生，里面包含了作用在这个组件上的所有监听器，从而不必再使用native修饰符 -->
    {{listeners}}
    <EventCompL v-on:focus="onFocus" v-model="listeners"></EventCompL>
    <EventBusCompA></EventBusCompA>
    <EventBusCompB></EventBusCompB>
    <InjectionComp></InjectionComp>
  </div>
</template>

<script>
import Static from './components/propsTransfer/Static'
import Dynamic from './components/propsTransfer/Dynamic'
import PropValidator from './components/propsTransfer/PropValidator'
import NoPropsAttribute from './components/propsTransfer/NoPropsAttribute'
import EventComp from './components/customEventsOfComp/EventComp'
import EventCompM from './components/customEventsOfComp/EventCompM'
import EventCompL from './components/customEventsOfComp/EventCompL'
import EventBusCompA from './components/eventBus/EventBusCompA'
import EventBusCompB from './components/eventBus/EventBusCompB'
import InjectionComp from './components/provideAndInject/InjectionComp'
export default {
  name: 'App',
  data() {
    return {
      message: 'string',
      listeners: 'listeners',
      timer: null,
      timeNum: 60,
      obj: {
        id: 1,
        context: 'i am obj'
      },
      arr: [1, 2],
      propString: 'i am prop string',
      propsArr: [1,2,3]
    }
  },
  methods: {
    onChange(inputValue) {
      console.info(inputValue)
    },
    onFocus() {
      console.info('child EventCompL input is focused')
    }
  },
  mounted() {
    this.timer = setInterval(() => {
      if(this.timeNum === 1) {
        clearInterval(this.timer)
        this.timer = null
      }
      this.timeNum -= 1
    }, 1000)
  },
  beforeDestroy(){
    clearInterval(this.timer)
    this.timer = null
  },
  components: {
    Static,
    Dynamic,
    PropValidator,
    NoPropsAttribute,
    EventComp,
    EventCompM,
    EventCompL,
    EventBusCompA,
    EventBusCompB,
    InjectionComp
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
