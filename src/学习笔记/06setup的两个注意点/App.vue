<template>
  <div class="app">
    <BaseDemo msg='你好啊' company='联蔚' @sendFather="getFather">
      <template v-slot:qwe>
        <span>插槽2</span>
      </template>
      <!-- <template slot='qwe'>
        <span>插槽2</span>
      </template> -->
      <span>插槽1</span>
    </BaseDemo>
  </div>
</template>

<script>
import BaseDemo from '@/components/BaseDemo.vue'

export default {
  components: {
    BaseDemo
  },
  setup() {
    function getFather(v) {
      console.log('接收到子组件传递过来的name -- ',v);
    }
    return {
      getFather
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
