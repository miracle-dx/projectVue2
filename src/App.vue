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
  </div>
</template>

<script>
import Static from './components/propsTransfer/Static'
import Dynamic from './components/propsTransfer/Dynamic'
import PropValidator from './components/propsTransfer/PropValidator'
import NoPropsAttribute from './components/propsTransfer/NoPropsAttribute'

export default {
  name: 'App',
  data() {
    return {
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
    NoPropsAttribute
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
