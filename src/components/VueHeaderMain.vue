<script>
import HeaderTop from './HeaderTop.vue'
import HeaderBottom from './HeaderBottom.vue'

export default {
  data() {
    return {
    }
  },
  name: 'VueHeaderMain',
  components: {
    HeaderTop,
    HeaderBottom,
  }
}
</script>

<template>
  <div class="VueHeaderMain">
    <HeaderTop />
  </div>
  <div class="container">
    <div class="wrapper">
      <HeaderBottom />
    </div>
  </div>
</template>

<style scoped>
.VueHeaderMain {
  width: 100%;
}
.container {
  background-color: #fff;
  z-index: 10;
  position: sticky;
  top: 0;
  left: 0;
}
.wrapper {
  padding: 0px 40px;
  margin: 0 auto;
  max-width: 1200px;
}

/*-----------------------------Media---------------------*/

@media (max-width: 1280px) {}

@media (max-width: 1024px) {
  .wrapper {
    padding: 0px 72px;
  }
}

@media (max-width: 768px) {
  .wrapper {
    padding: 0px 16px;
  }
}
</style>
