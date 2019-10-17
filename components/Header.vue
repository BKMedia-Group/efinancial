<template>
  <header>
    <div class="container">
      <img src="~/assets/images/logo.svg" />
      <Button url="#">Enroll Today</Button>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  padding: 30px 0;
  .container {
    display: flex;
    img {
      margin-right: auto;
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
