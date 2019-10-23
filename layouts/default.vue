<template>
  <div>
    <Header />
    <nuxt />
    <Footer />
  </div>
</template>
<script>
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'
require('vue-scrollto')
export default {
  components: {
    Header,
    Footer
  }
}
</script>
