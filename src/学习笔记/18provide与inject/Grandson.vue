<template>
  <div class="Grandson">
    孙子：{{ name }} --- {{ price }}
  </div>
</template>

<script>
import { inject, toRefs } from 'vue'
export default {
  setup () {
    let car = inject('car')
    console.log(car);
    return {
      ...toRefs(car)
    }
  }
}
</script>
<style lang="scss">
.Grandson {
  background-color: lightblue;
  padding: 10px;
}
</style>
