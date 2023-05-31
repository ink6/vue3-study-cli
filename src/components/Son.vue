<template>
  <div class="son">
    儿子组件
    <Grandson></Grandson>
  </div>
</template>

<script>
import { reactive } from 'vue'
import Grandson from './Grandson.vue'
export default {
  components: { Grandson },
  setup () {
  }
}
</script>
<style lang="scss">
.son {
  background-color: lightgoldenrodyellow;
  padding: 10px;
}
</style>
