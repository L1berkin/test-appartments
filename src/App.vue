<template>
  <div id="app">
    <main-header />
    <wrapper>
      <div
        v-if="loading"
        class="loader-container"
      >
        <base-loader />
      </div>
      <appartments-list
        v-else
        :appartments="apps"
      />
    </wrapper>
  </div>
</template>

<script>
import AppartmentsList from './components/AppartmentsList.vue';
import BaseLoader from './components/BaseLoader.vue';
import Wrapper from './components/hoc/Wrapper.vue';
import MainHeader from './components/MainHeader.vue';

export default {
  name: 'App',
  components: {
    MainHeader,
    Wrapper,
    AppartmentsList,
    BaseLoader,
  },
  data() {
    return {
      loading: true,
      apps: [],
    };
  },
  mounted() {
    const appartments = localStorage.getItem('appartments');
    if (appartments) {
      this.apps = JSON.parse(appartments).data;
    } else {
      this.createApps();
      const body = {
        data: this.apps,
      };
      localStorage.setItem('appartments', JSON.stringify(body));
    }
    setTimeout(() => {
      this.loading = false;
    }, 1000);
  },
  methods: {
    createApps() {
      for (let i = 1; i <= 10; i += 1) {
        const price = `${Math.round(Math.random() * 1000) * 10000}`;
        const area = `${Math.round(Math.random() * 1000)}`;
        const appart = {
          number: i,
          price,
          area,
          title: `Квартира ${i}`,
          liked: false,
        };
        this.apps.push(appart);
      }
    },
  },
};
</script>

<style>
@import './assets/styles/main.css';
.loader-container {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 30px;
}
</style>
