<template>
  <h2>从定义数据的角度</h2>
  <p>ref：用来定义：基本数据类型 + 引用数据类型</p>
  <p>reactive: 用量定义引用（对象、数组）类型</p>
  <p>ref也可以用来定义引用数据类型，它内部会自动通过reactive转换为代理对象</p>
  <hr>
  <h2>从原理角度</h2>
  <p>ref通过Object.defineProperty的get和set来实现响应式（数据劫持）</p>
  <p>reactive通过使用Proxy来实现响应式（数据劫持），并通过Reflect操作源对象内部的数据</p>
  <hr>
  <h2>从使用角度</h2>
  <p>ref定义的数据：操作需要.value, 读取数据时模板不需要.value</p>
  <p>reactive定义的数据：操作数据或读取数据均不需要.value</p>
</template>

<script>
export default {
  setup(props){
    
  }
}
</script>
<style lang="scss">
</style>
