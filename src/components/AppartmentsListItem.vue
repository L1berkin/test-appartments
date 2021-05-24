<template>
  <div class="appartments">
    <appartments-photo
      v-if="openPhoto"
      :numberPhoto="element.number"
      @close="openPhoto = false"
    />
    <div class="appartments__photo-container">
      <img
        :src="require(`../assets/appartments/${element.number}.jpg`)"
        alt="квартира"
        class="appartments__photo"
        @click="openPhoto = true"
      >
    </div>
    <h4 class="appartments__title">
      {{ element.title }}
    </h4>
    <div class="appartments__body">
      <div class="settings">
        <p class="settings__item">
          Площадь: {{ element.area }} кв.
        </p>
        <p class="settings__item">
          Цена: <strong>{{ element.price }}</strong> руб.
        </p>
      </div>
      <button
        class="appartments__btn"
        :class="{liked: liked}"
        @click="like"
      >
        <img src="../assets/icons/icon-like.png" alt="нравится">
        Like
      </button>
    </div>
  </div>
</template>

<script>
import AppartmentsPhoto from './AppartmentsPhoto.vue';

export default {
  components: { AppartmentsPhoto },
  name: 'AppartmentsListItem',
  props: {
    element: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      openPhoto: false,
      liked: false,
    };
  },
  mounted() {
    this.liked = this.element.liked;
  },
  methods: {
    like() {
      this.liked = !this.liked;
      const { data } = JSON.parse(localStorage.getItem('appartments'));
      data[this.element.number - 1].liked = !data[this.element.number - 1].liked;
      const newData = {
        data: [
          ...data,
        ],
      };
      localStorage.setItem('appartments', JSON.stringify(newData));
    },
  },
};
</script>

<style scoped>
.appartments {
  width: 100%;
  max-width: 380px;
  margin: 0 auto;
  padding: 10px;
  border-radius: 10px;
  box-shadow: 0 0 10px -5px #000;
  transition: .3s;
}

.appartments__photo-container {
  width: 100%;
  height: 250px;
  overflow: hidden;
}

.appartments__photo {
  width: 100%;
  height: 100%;
  cursor: pointer;
  border-radius: 5px;
}

.appartments__title {
  margin: 15px 0 20px;
  font-size: 1.2rem;
  font-weight: bold;
}

.appartments__body {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

.settings {
  flex-grow: 1;
}

.settings__item {
  margin: 10px 0;
}

.appartments__btn {
  padding: 15px 20px;
  margin-left: 15px;
  transition: .3s;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 5px 10px -5px #000;
}

.appartments__btn:hover {
  box-shadow: 0 5px 10px -5px #00b0ff;
}

.appartments__btn:active {
  transform: translateY(5px);
  box-shadow: 0 0 10px -5px #00b0ff, inset 0 0 10px -5px #00b0ff;
}

.liked {
  background: rgba(0, 174, 255, 0.2);
  transform: translateY(5px);
  box-shadow: 0 0 10px -5px #00b0ff;
}

.liked:hover {
  background: rgba(0, 174, 255, 0.1);
  box-shadow: 0 0 10px -7px #00b0ff;
}

@media screen and (max-width: 1200px) {
  .appartments__photo-container {
    height: 200px;
  }
}

@media screen and (max-width: 1050px) {
  .appartments__btn {
    width: 100%;
    margin: 10px 0;
  }
}

@media screen and (max-width: 930px) {
  .appartments__photo-container {
    height: 250px;
  }
}

@media screen and (max-width: 680px) {
  .appartments__photo-container {
    height: 180px;
  }
}

@media screen and (max-width: 530px) {
  .appartments__photo-container {
    height: 250px;
  }
}
</style>
