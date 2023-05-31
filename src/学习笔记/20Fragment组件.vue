<template>
  <div class="app">
    <h2>Fragment</h2> 
    <p>在vue2中 组件必须有一个根标签</p>
    <p>在vue3中 组件可以没有跟标签 内部会将多个标签包在一个Fragment虚拟列表中</p>
    <p>好处：减少标签层级，减少内存占用</p>
  </div>
</template>

<script>
</script>
<style lang="scss">
.app {
  background-color: lightcoral;
  padding: 10px;
}
</style>
