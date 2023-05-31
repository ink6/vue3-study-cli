<template>
  <div class="app">
    
  </div>
</template>

<script>
import { reactive, ref, toRefs, readonly, isRef, isReactive, isReadonly, isProxy } from 'vue'
export default {
  setup () {
    const car = reactive({ name: '奔驰', price: '14w'})
    const sum = ref(0)
    const car2 = readonly(car)
    const refCar = ref({ name: '奔驰', price: '14w'})
    console.log(isRef(car));
    console.log(isRef(sum));
    console.log(isRef(refCar));
    console.log('----------------isRef');
    console.log(isReactive(car));
    console.log(isReactive(sum));
    console.log(isReactive(refCar));
    console.log('----------------isReactive');
    console.log(isReadonly(refCar));
    console.log(isReadonly(car));
    console.log(isReadonly(car2));
    console.log('----------------isReadonly');
    console.log(isProxy(car));
    console.log(isProxy(sum));
    console.log(isProxy(car2));
    console.log(isProxy(refCar));
    console.log(refCar, isProxy(refCar.value));
    console.log('----------------isProxy');

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
