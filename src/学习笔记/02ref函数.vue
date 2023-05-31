<template>
  <h1>ref函数</h1>
  <h2>ref 可以用来定义一个响应式的数据， 接收的对象可以是基本类型 也可以是对象类型</h2>
  <h2>基本数据：响应式依然是靠的Object.defineProperty的get与set完成的， 与vue2相同</h2>
  <h2>引用数据：内部“求助”了Vue3中的一个新函数 - reactive函数，底层是基于ES6的Proxy实现的</h2>
  <h4>我叫{{ name }}， 我今年 {{ age }}岁了，我的年薪是 {{salary.main + salary.other }} 万</h4>
  <button @click="addSalary">给薛雯婷涨薪</button>
</template>

<script>
import { ref } from 'vue'
export default {
  setup(props){
    /**
     * * ref函数处理基本类型
     * name => RefImpl {__v_isShallow: false, dep: undefined, __v_isRef: true, _rawValue: '薛雯婷', _value: '薛雯婷'}
     * ref包裹后是个对象，是refImpl的实例对象 
     * refImpl是 reference+implement译为引用实现。也就是说在vue3里面，如果想把字符串、整数这类基本数据类型变成响应式的，应该用ref函数包裹，也就是把该基本数据类型变成引用实现的实例对象。
     * eg: name => RefImpl => Reference(引用) + implement(实现) => 则name是引用实现的实例引用对象，简称ref对象
     * ref包裹基本数据类型，也就是给该基本数据类型加上getter，读取vue源码可知，在vue3中，也是通过defineobjectproperty实现基本数据类型的响应式
     */
    const name = ref('薛雯婷')
    const age = ref(18)
    const salary = ref({
      main: 1,
      other: 1
    })
    console.log(name, age, salary);
    // salary 是一个RefImpl 其中的.value 是Proxy包裹的main 和 other 
    // 实际上在vue3里面处理引用数据类型变成响应式用的是proxy代理，也就是说表面上ref可以包裹引用数据类型，实际上vue3调用的是reactive, 所以这里不需要再main.value
    function addSalary () {
      salary.value.main ++
      // console.log(person, person3);
    }


    // setup的返回值 是一个对象 那么数据，方法在模板中可以直接使用
    return {
      name,
      age,
      salary,
      addSalary,
    }
  }
}
</script>
<style lang="scss">
</style>
