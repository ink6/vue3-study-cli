<template>
  <div class="app">
    <h4>数值是： {{ num }}</h4>
    <button @click="num ++">点我+1</button>
    <hr>
    <h4>文案是：{{ msg }}</h4>
    <button @click="msg += '~!!'">点我+1</button>
    <hr>
    <h2>个人信息</h2>
    <h2>姓名：{{ name }} </h2>
    <button @click="name += '~'">修改姓名</button> 
    <hr>
    <h2>年龄：{{ age }} </h2>
    <button @click="age ++">增加年龄</button> 
    <hr>
    <h2>薪资：{{ job.salary.amway }} K</h2>
    <button @click="job.salary.amway  ++">涨薪</button>
  </div>
</template>

<script>
import { ref, toRefs, reactive, watchEffect } from 'vue'

export default {
  setup(){
    /**
     * * watch & watchEffect 对比
     * watch：既要指明监视的属性，也要指明监视的回调
     * watchEffect: 不用指明监视的是哪个属性，监视的回调中用到哪个属性，那就监视哪个属性
     * 
     * * watchEffect & computed
     * watchEffect与computed有点类似
     * 1、但computed 更注重计算出来的值（回调函数的返回值），所以必须要写返回值
     * 2、而watchEffect 更注重的是过程（回调函数的函数体），所以不用写返回值
     */
    const num = ref(0)
    const msg = ref('薛雯婷好美啊')
    const person = reactive({
      name: '薛雯婷',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      }
    })
    // watchEffect所指定的回调中用到的数据如果发生变化，则直接重新执行回调
    watchEffect(() => {
      const res1 = num.value
      const res2 = person.name
      console.log('watchEffect配置的回调执行了', res1, res2);
    })
    return {
      num,
      msg,
      ...toRefs(person),
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
