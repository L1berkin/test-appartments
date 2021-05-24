<template>
  <div
    class="background"
    @click="$emit('close')"
  >
    <img
      src="../assets/icons/icon-close.svg"
      alt="закрыть"
      class="icon-close"
    >
    <div class="appartments-photo">
      <img
        :src="require(`../assets/appartments/${numberPhoto}.jpg`)"
        alt="квартира"
        class="appartments-photo__photo"
        @click.stop
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'Appartments-photo',
  props: {
    numberPhoto: {
      type: Number,
      default: 1,
    },
  },
  mounted() {
    document.querySelector('html').style = 'overflow: hidden';
  },
  beforeDestroy() {
    document.querySelector('html').style = '';
  },
};
</script>

<style scoped>
.background {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.6);
  z-index: 5;
}

.appartments-photo {
  width: 60%;
  margin-top: 30px;
  transform: translateY(-150%);
  animation: slideDown .6s ease-in-out 0s forwards 1;
}

.appartments-photo__photo {
  width: 100%;
}

.icon-close {
  position: absolute;
  right: 50px;
  top: 30px;
  cursor: pointer;
}

@keyframes slideDown {
  0% {
    transform: translateY(-150%);
  }
  100% {
    transform: translateY(0);
  }
}
</style>
