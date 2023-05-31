<template>
  <div class="app">
    <h2>个人信息</h2>
    <h4>姓：<input type="text" v-model="lastName"></h4>
    <h4>名：<input type="text" v-model="firstName"></h4>
    <h4>这个人的姓名是： {{fullName}}</h4>
    <h4>全名：<input type="text" v-model="fullName"></h4>

    <hr>
  </div>
</template>

<script>
import { toRefs, reactive, computed } from 'vue'

export default {
  setup(props, { emit, attrs, slots }){ // setup的执行在beforeCreate之前 context-上下文
    const person = reactive({
      firstName: '雯婷',
      lastName: '薛'
    })
    // 计算方法 - 简写
    // person.fullName = computed(() => person.lastName + '-' + person.firstName)
    person.fullName = computed({
      get() {
        return person.lastName + '-' + person.firstName
      },
      set(value) {
        console.log(value);
        const names = value.split('-')
        person.firstName = names[1]
        person.lastName = names[0]
      }
    })

    console.log(person);
    return {
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
