<template>
  <div class="app">
    <h2>个人信息</h2>
    <h2>数值： {{ sum }}</h2>
    <h2>姓名：{{ name }} </h2>
    <h2>年龄：{{ age }} </h2>
    <h2>薪资：{{ job.salary.amway }} K</h2>
    <h3 v-show="person.car">车辆信息：{{ person.car }}</h3>
    <hr>
    <button @click="name += '~'">修改姓名</button> 
    <button @click="age ++">增加年龄</button> 
    <button @click="job.salary.amway  ++">涨薪</button>
    <button @click="getRowData">点我获取初始的数据</button>
    <button @click="addCar">给温蒂添加一台车</button>
    <div v-if="person.car">
      <button @click="person.car.name += '~'">修改车品牌</button>
      <button @click="person.car.price ++ ">修改车价格</button>
    </div>
  </div> 
</template>

<script>
import { toRefs, reactive, ref, toRaw, markRaw } from 'vue'
export default {
  /**
   * toRaw
   * 作用： 将一个由reactive生成的对象转为普通对象
   * 使用场景：用于读取响应式对象对应的普通对象，对这个普通对象的所有操作，不会引起页面的更新
   * markRaw
   * 作用： 标记一个对象，使其永远不会再成为响应式对象
   * 使用场景：
   *  1、有些值不应被设为响应式的，例如复杂的第三方类库等
   *  2、当渲染具有不可变数据源的大列表时，跳过响应式转换可以提高性能
   */
  setup(){
    let sum = ref(0)
    let refObj = ref({
      a: {
        o: 'A'
      }
    })
    let person = reactive({
      name: '温蒂',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      },
      // car: {}
    })

    function getRowData () {
      const people = toRaw(person)
      console.log(people);
      // const sum1 = toRaw(sum)
      // console.log(sum1);
      const _refObj = toRaw(refObj)
      console.log(_refObj);
    }

    function addCar () {
      // 向proxy追加的 是响应式的数据
      const car = { 'name': '宝马', 'price': 2 } // 这样直接添加是响应式数据，但是在dom无法展示，因为setup执行时，没有car, 两种方式1、在person里定义好空的car 2、将person抛出去，在dom里person.car
      // person.car = car
      person.car = markRaw(car)
      console.log(person);

    }
    return {
      sum,
      getRowData,
      addCar,
      person,
      ...toRefs(person)
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 40px;
}
</style>
