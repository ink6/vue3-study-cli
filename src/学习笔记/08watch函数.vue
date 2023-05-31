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
import { ref, toRefs, reactive, watch } from 'vue'

export default {
  setup(){
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
    /**
     * * watch函数
     * * 与vue2中的watch配置功能一致
     * * 两个小坑： 
     * * 1、监听reactive定义的响应式数据时，oldValue无法正确读取，且强制开启了深度监听（{deep:true/false}配置失效）
     * * 2、监视reactive定义的响应式数据中的某个属性时：deep配置有效 但是这个属性必须是引用数据类型，若是基本数据类型 配置deep没有意义
     */
    // 情况一： 监视ref定义的响应式数据（基本类型）
    // watch(num, (newValue, oldValue) => {
    //   console.log(`有人修改了num, 新值为${newValue}, 旧值为${oldValue}`);
    // })
    // watch(msg, (newValue, oldValue) => {
    //   console.log(`有人修改了msg, 新值为${newValue}, 旧值为${oldValue}`);
    // })

    // 情况二： 监视多个ref定义的响应式数据（基本类型）
    // watch([num, msg], (newValue, oldValue) => {
    //   console.log('有人修改了num或msg, 新值为: ', newValue, '旧值为:', oldValue);
    // })

    // 情况三： 监视reactive定义的响应式数据, 无法正确的获取oldValue,且强制开启了深度监视
    // watch(person, (newValue, oldValue) => {
    //   console.log('有人修改了person, 新值为: ', newValue, '旧值为:', oldValue);
    // }, { immediate: true, deep: true }) // deep： true配置无效

    // 情况四：监视reactive所定义的一个响应式数据中的某个属性
    // watch(()=>person.name, (newValue, oldValue) => {
    //   console.log('有人修改了person.name, 新值为: ', newValue, '旧值为:', oldValue);
    // })

    // 情况五：监视reactive所定义的一个响应式数据中的某些属性
    // watch([()=>person.name,()=>person.age], (newValue, oldValue) => {
    //   console.log('有人修改了person.name或person.age, 新值为: ', newValue, '旧值为:', oldValue);
    // }, { immediate: true })

    // 特殊情况： 
    watch(()=> person.job, (newValue, oldValue) => {
      console.log('有人修改了person.job, 新值为: ', newValue, '旧值为:', oldValue);
    }, { deep: true }) //此处由于监视的是reactive所定义的某个属性，所以配置deep true有效，但是这个属性必须是引用数据类型，若是基本数据类型 配置deep无意义

    
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
