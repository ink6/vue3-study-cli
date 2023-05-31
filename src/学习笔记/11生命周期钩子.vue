<template>
  <div class="app">
    <h2>我的BaseDemo组件</h2>
    <h2>数值是： {{ num }}</h2>
    <button @click="num +=1 ">点我 + 1</button>
  </div>
</template>

<script>
import { onBeforeMount, onMounted, onBeforeUnmount, onUnmounted, onBeforeUpdate, onUpdated, onActivated, onDeactivated, ref } from 'vue';
export default {
  /**
   * beforeCreate - setup
   * created - setup
   */
  beforeCreate () {
    console.log(' --- vue2 --- beforeCreate --- ');
  },
  created () {
    console.log(' --- vue2 --- created --- ');
  },
  beforeMount () {
    console.log(' --- vue2 --- beforeMount --- ');
  },
  mounted () {
    console.log(' --- vue2 --- mounted --- ');
  },
  beforeUpdate() {
    console.log(' --- vue2 --- beforeUpdate --- ');
  },
  updated() {
    console.log(' --- vue2 --- updated --- ');
  },
  activated () {
    console.log(' --- vue2 --- activated --- ');
  }, 
  deactivated () {
    console.log(' --- vue2 --- deactivated --- ');
  },
  // 弃用
  // beforeDestroy() {
  //   console.log(' --- vue2 --- beforeDestroy --- ');
  // },
  // destroyed() {
  //   console.log(' --- vue2 --- destroyed --- ');
  // },
  beforeUnmount() {
    console.log(' --- vue2 --- beforeUnmount --- ');
  },
  unmounted() {
    console.log(' --- vue2 --- unmounted --- ');
  },
  setup(){
    console.log(' --- vue3 --- setup --- 在beforeCreate之前');
    onBeforeMount(() => {
      console.log(' --- vue3 --- onBeforeMount --- ');
    }),
    onMounted(() => {
      console.log(' --- vue3 --- onMounted --- ');
    }),
    onBeforeUpdate(() => {
      console.log(' --- vue3 --- onBeforeUpdate --- ');
    }),
    onUpdated(() => {
      console.log(' --- vue3 --- onUpdated --- ');
    }),
    /**
     * 父组件
     * <keep-alive>
     *  <BaseDemo v-if="showBaseDemo"/>
     * </keep-alive>
     */
    onActivated(() => {
      console.log(' --- vue3 --- onActivated --- ');
    })
    onDeactivated(() => {
      console.log(' --- vue3 --- onDeactivated --- ');
    })
    onBeforeUnmount(() => {
      console.log(' --- vue3 --- onBeforeUnmount --- ');
    }),
    onUnmounted(() => {
      console.log(' --- vue3 --- onUnmounted --- ');
    })

    const num = ref(0)
    return {
      num
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
