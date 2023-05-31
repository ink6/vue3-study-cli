<template>
  <div class="app">
    <h2>个人信息</h2>
    <h2>姓名：{{ person.name }} </h2>
    <button @click="person.name += '~'">修改姓名</button> 
    <hr>
    <h2>年龄：{{ person.age }} </h2>
    <button @click="person.age ++ ">增加年龄</button> 
    <hr>
    <h2>薪资：{{ person.job.salary.amway }} K</h2>
    <button @click="person.job.salary.amway  ++ ">涨薪</button>
  </div>
</template>

<script>
import { ref, watch } from 'vue'

export default {
  setup(){
    const person = ref({
      name: '薛雯婷',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      }
    })
    // 情况七：监视ref所定义的一个引用类型的响应式数据
    // 1、需要监视person.value 因为watch 只能监听ref对象或reactive对象 此处监听.value 相当于监听了reactive对象
    // watch(person.value, (newValue, oldValue) => {
    //   console.log('有人修改了person, 新值为: ', newValue, '旧值为:', oldValue);
    // })
    
    // 2、开启深度监视，相当于监视refImpl下的所有深层次属性，其中包括.value属性
    watch(person, (newValue, oldValue) => {
      console.log('有人修改了person, 新值为: ', newValue, '旧值为:', oldValue);
    }, { deep: true }) // 此处无法正确的获取oldValue,且强制开启了深度监视

    return {
      person,
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
