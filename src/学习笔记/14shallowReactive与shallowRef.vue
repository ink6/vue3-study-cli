<template>
  <div class="app">
    <h2>个人信息</h2>
    {{ person1 }}
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
import { toRefs, reactive, shallowReactive, shallowRef } from 'vue'
export default {
  setup(){
    /**
     * shallowReactive 与 shallowRef
     * shallowReactive： 只处理对象最外层属性的响应式（浅响应式）
     * shallowRef: 只处理基本数据类型的响应式（基本数据类型时与ref一模一样），不进行对象的响应式处理（包裹对象类型会使其变成最普通的Object）
     * 什么时候使用？
     *   如果有一个对象数据， 结构比较深，但是变化时只是最外层属性变化 => shallowReactive
     *   如果有一个对象数据，后续功能不会修改该对象中的属性，而是生成新的对象来替换 => shallowRef
     */
    // const person = reactive({
    //   name: '薛雯婷',
    //   age: 18,
    //   job: {
    //     salary: {
    //       amway: 1
    //     }
    //   }
    // })
    const person = shallowReactive({
      name: '薛雯婷',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      }
    })
    const person1 = shallowRef({ // RefImlp{....value} => value 是普通的Object
      name: '薛雯婷',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      }
    })
    console.log(person1);
    return {
      person1,
      ...toRefs(person)
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
