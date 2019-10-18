<template>
  <a :href="url"><slot></slot></a>
</template>

<script>
export default {
  props: {
    url: String
  }
}
</script>

<style lang="scss" scoped>
a {
  display: inline-block;
  color: #ffffff;
  background: #ff671b;
  padding: 18px 25px;
  border-radius: 25px;
  text-decoration: none;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: 500;
  letter-spacing: 1px;
  line-height: 16px;
  text-align: center;
  @media (max-width: 480px) {
    padding: 11px 25px;
  }
}
</style>
