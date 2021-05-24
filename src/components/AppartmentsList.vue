<template>
  <section class="appartments-container">
    <appartments-list-item
      v-for="el in appartments"
      :key="el.number"
      :element="el"
    />
  </section>
</template>

<script>
import AppartmentsListItem from './AppartmentsListItem.vue';

export default {
  components: { AppartmentsListItem },
  name: 'AppartmentsList',
  props: {
    appartments: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style scoped>
.appartments-container {
  margin-top: 50px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 50px;
}

@media screen and (max-width: 930px) {
  .appartments-container {
    grid-template-columns: 1fr 1fr;
    gap: 30px;
  }
}

@media screen and (max-width: 530px) {
  .appartments-container {
    grid-template-columns: 1fr;
    gap: 30px;
  }
}
</style>
