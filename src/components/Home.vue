<template>
  <div class="home">
    <Loading :imgSrc="imgSrc" :bgSrc="bgSrc"></Loading>
    <span>这是一些测试文字</span>
  </div>
</template>

<script>
import Loading from './Loading'
export default {
  name: 'home',
  components: {
    Loading
  },
  data () {
    return {
      imgSrc: 'http://odhxwvue8.bkt.clouddn.com/new%20logo_square.jpg',
      bgSrc: 'https://nkmun.cn/img/background.jpg'
    }
  }
}
</script>

<style>
body {
  margin: 0;
  background: url('https://nkmun.cn/img/background.jpg');
}
</style>
