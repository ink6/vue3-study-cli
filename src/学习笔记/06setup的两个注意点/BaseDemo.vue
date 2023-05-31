<template>
  <div class="app">
    <h2>个人信息</h2>
    <h4>姓名：{{ name }}</h4>
    <h4>年龄：{{ age }}</h4>
    <button @click="emitFather">传递到父组件</button>
    <hr>
    <slot></slot>
    <slot name='qwe'></slot>
  </div>
</template>

<script>
import { toRefs, reactive } from 'vue'

export default {
  /**
   * * setup的两个注意点
   * * !setup的执行时机
   * * 在beforeCreate之前执行一次，this是undefined
   * * !setup的参数
   * * props： 值为对象，包含：组件外包传递过来切组件内部声明接收了的属性
   * * context: 上下文对象
   * * attrs: 值为对象，包含：组件外部传递过来，但是没有在组件内部声明接收的属性，相当于vue2的this.$attrs
   * * emit: 分发自定义事件的内容，相当于this.$slots
   * * slots: 收到的插槽内容，相当于this.$slots
   */
  // beforeCreate() {
  //   console.log('v2 --- beforeCreate ---');
  // },
  // created() {
  //   console.log('v2 --- created ---');
  // },
  // props: ['msg', 'company'],
  // emits: ['sendFather'],
  setup(props, { emit, attrs, slots }){ // setup的执行在beforeCreate之前 context-上下文
    // console.log('v3 --- setup ---, this是', this);
    console.log('props', props);
    console.log('emit', emit);
    console.log('attrs', attrs);
    console.log('slots', slots);
    // 当没有定义props的时候， attrs的内容包含父组件传递过来的props的内容
    // console.log(attrs, attrs.msg, attrs.company);
    const person = reactive({
      name: '薛雯婷',
      age: 18,
    })
    function emitFather () {
      console.log('传递给父组件', person.name);
      emit('sendFather', person.name)
    }
    return {
      ...toRefs(person),
      emitFather
    }
  }
}
</script>
<style lang="scss">
.app {
  background-color: lightpink;
  padding: 10px;
}
</style>
