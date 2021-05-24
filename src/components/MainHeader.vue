<template>
  <header class="header">
    <img
      class="header__logo"
      src="../assets/main-logo.png"
      alt="логотип"
    >
    <h2 class="header__title">
      Квартирка
    </h2>
  </header>
</template>

<script>
export default {
  name: 'MainHeader',
};
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  height: 60px;
  background: #fff;
  box-shadow: 0 0 10px 0 #000;
}

.header__logo {
  height: 50px;
  margin: 5px 20px 5px 5%;
}

.header__title {
  font-size: 1.4rem;
}
</style>
