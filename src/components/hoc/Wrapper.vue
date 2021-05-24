<template>
  <div class="wrapper">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Wrapper',
};
</script>

<style scoped>
.wrapper {
  width: 80%;
  max-width: 1400px;
  margin: 0 auto;
}

@media screen and (max-width: 1200px) {
  .wrapper {
    width: 90%;
  }
}
</style>
