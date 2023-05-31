<template>
  <div class="app">
    <!-- <h2>teleport</h2> 
    <p>什么是Teleport? Teleport是一种能够将我们的组件html结构移动到指定位置的技术</p> -->
    <Dialog></Dialog>
  </div>
</template>

<script>
import Dialog from '@/components/Dialog.vue'
export default {
  components: { Dialog },
}

</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
