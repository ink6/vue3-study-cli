<template>
  <h4>我叫{{ person.name }}， 我今年 {{ person.age }}岁了，我的年薪是 {{person.salary.main + person.salary.other }} 万</h4>
  <h4>我叫{{ name }}， 我今年 {{ age }}岁了，我的年薪是 {{ salary.main + salary.other }} 万</h4>
  <button @click="addSalary">给薛雯婷涨薪</button>

</template>

<script>
import { toRefs, reactive } from 'vue'
export default {
  
  setup(props){
    /**
     * 拿reactive定义基础数据类型-> 会得到一个警告
     */
    // const number = reactive(666) // reactivity.esm-bundler.js?89dc:951 value cannot be made reactive: 666
    /**
     * reactive 定义的响应式数据 是深层次的
     * 内部基于ES6的Proxy实现，通过代理对象操作源对象内部数据进行操作
     */
    
    const person = reactive({
      name: '薛雯婷',
      age: 18,
      salary: {
        main: 1,
        other: 1
      }
    })
    function addSalary () {
      person.salary.main ++
      console.log(person, {...toRefs(person)});
    }

    return {
      person,
      ...toRefs(person),
      addSalary,
    }
  }
}
</script>
<style lang="scss">
</style>
