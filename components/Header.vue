<template>
  <header>
    <div class="container">
      <a href="/" class="logo">
        <img src="~/assets/images/logo.svg" />
      </a>
      <Button v-scroll-to="'#form'">Enroll Today</Button>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  padding: 30px 0;
  .container {
    display: flex;
    align-items: center;
    a.logo {
      margin-right: auto;
      img {
        height: 50px;
        width: auto;
        @media (max-width: 480px) {
          height: 30px;
        }
      }
    }
  }
}
</style>
<script>
import Button from '~/components/Button.vue'
export default {
  components: {
    Button
  }
}
</script>
