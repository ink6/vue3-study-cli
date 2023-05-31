<template>
  <div class="mask">
    <div class="body">
      <header>标题</header>
      <section>这是一个内容哦， 这个是一个内容哦</section>
      <footer>
        <a>确定</a>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
    return {}
  }
}
</script>

<style lang="scss" scoped>
.mask {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);
}
.body {
  position: absolute;
  // left: 0;
  // right: 0;
  // top: 0;
  // bottom: 0;
  width: 400px;
  height: 400px;
  background-color: #fff;
  margin: auto;
  padding: 40px;
  box-sizing: border-box;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
}
header {
  font-size: 28px;
  font-weight: bold;
  text-align: center;
}
footer {
  width: inherit;
  position: absolute;
  bottom: 0;
  text-align: center;
  a {
    display: inline-block;
    width: 100px;
    height: 44px;
    line-height: 44px;
    background-color: palevioletred;
    color: #fff;
    font-size: 22px;
    border-radius: 44px;
  }
}
</style>