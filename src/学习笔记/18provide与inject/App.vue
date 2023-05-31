<template>
  <div class="app">
    爷爷： {{ name }} --- {{ price }}
    <Son></Son>
  </div>
</template>

<script>
import { reactive, provide, toRefs } from 'vue'
import Son from '@/components/Son.vue'
export default {
  components: { Son },
  setup () {
    const car = reactive({ name: '奔驰', price: '14w'})
    provide('car', car)
    return {
      ...toRefs(car)
    }
  }
}
</script>
<style lang="scss">
.app {
  background-color: lightcoral;
  padding: 10px;
}
</style>
