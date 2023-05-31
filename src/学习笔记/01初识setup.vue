<template>
  <h2>Vue2的数据</h2>
  <h4>我是{{ personVue2.name }}， 我今年 {{ personVue2.age }}岁了，我喜欢 {{ personVue2.hobby }}</h4>
  <button @click="changeHobby">修改温蒂的爱好 - vue2拿vue3数据</button>
  <h2>Vue3的数据</h2>
  <h4>我叫{{ person1.name }}， 我今年 {{ person1.age }}岁了，我的年薪是 {{person1.salary.main + person1.salary.other }} 万</h4>
  <h4>我叫{{ person2.name }}， 我今年 {{ person2.age }}岁了，我的年薪是 {{person2.salary.main + person2.salary.other }} 万</h4>
  <h4>我叫{{ person3.name }}， 我今年 {{ person3.age }}岁了，我的年薪是 {{person3.salary.main + person3.salary.other }} 万</h4>
  <h4>我叫{{ name }}， 我今年 {{ age }}岁了，我的年薪是 {{ salary.main + salary.other }} 万</h4>
  <button @click="addSalary">给薛雯婷涨薪 - vue3拿vue2数据 - 拿不到</button>

  <h2>触发一个vue2 和 vue3都有的方法</h2>
  <button @click="switchWho">会执行谁？ - 如果有重名，会执行setup中的</button>
</template>

<script>
import { ref, toRefs, reactive, h } from 'vue'
export default {
  data() {
    return {
      personVue2: {
        name: '风之神 - 温蒂',
        age: 180,
        hobby: '唱歌'
      }
    }
  },
  methods: {
    changeHobby () {
      this.personVue2.hobby = '烹饪'
      console.log(this.person2, this.person3);
    },
    switchWho() {
      alert('我是vue2中的方法，vue3有个和我同名的')
    }
  },
  setup(props){
    // 一个简单的Object对象
    const person1 = {
      name: '薛雯婷',
      age: 18,
      salary: {
        main: 1,
        other: 1
      }
    }
    // 一个由ref封装的Object双向数据对象
    const person2 = ref({
      name: '薛雯婷',
      age: 18,
      salary: {
        main: 1,
        other: 1
      }
    })
    // 一个由reactive封装的Object双向数据对象
    const person3 = reactive({
      name: '薛雯婷',
      age: 18,
      salary: {
        main: 1,
        other: 1
      }
    })
    function addSalary () {
      person2.value.salary.main ++
      person3.salary.main ++
      // console.log(person2, person3);
      // console.log(personVue2); // ERROR: personVue2 is not defined
    }

    function switchWho() {
      alert('我是Vue3中的方法，Vue2有个和我同名的')
    }

    // setup的返回值 是一个对象 那么数据，方法在模板中可以直接使用
    return {
      person1,
      person2,
      person3,
      ...toRefs(person3),
      addSalary,
      switchWho
    }

    // setup的返回值 是一个函数 可以自定义渲染内容
    // return () => {
    //   return h('p', '孤独的薛文婷')
    // }
    // 简写
    // return () => h('p', '孤独的薛文婷')
  }
}
</script>
<style lang="scss">
</style>
