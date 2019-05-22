<template>
  <div class="big-header">
    <img class="background" :src="background">
    <div class="wrapper">
      <h1 class="message">{{ message }}</h1>
      <div class="wrapper--buttons">
        <router-link v-if="button1" class="button button1" :to="route1">{{ button1 }}</router-link>
        <router-link v-if="button2" class="button button2" :to="route2">{{ button2 }}</router-link>
        <router-link v-if="button3 && show" class="button button3" :to="route3">{{ button3 }}</router-link>
        <router-link v-if="button4" class="button4" :to="route1"><button class="button" @click="map">{{ button4 }}</button></router-link>
      </div>
      <audio src="" autoplay refs="audio"></audio>
    </div>
  </div>
</template>


<script>
const data = require("../json/data.json");
import countService from '../json/countServices';
import saveBoussole from '../json/saveBoussole.js';
import saveEpee from '../json/saveEpee.js';
import saveMap from '../json/saveMap.js';

export default {
  computed: {
    route1() {
      return `${data[this.$route.params.id].choix1}`;
    },
    route2() {
      return `${data[this.$route.params.id].choix2}`;
    },
    route3() {
      return `${data[this.$route.params.id].choix3}`;
    },
    message() {
      return `${data[this.$route.params.id].text}`;
    },
    button1() {
      return `${data[this.$route.params.id].button1}`;
    },
    button2() {
      return `${data[this.$route.params.id].button2}`;
    },
    button3() {
      return `${data[this.$route.params.id].button3}`;
    },
    button4() {
      return `${data[this.$route.params.id].button4}`;
    },
    background() {
      return `${data[this.$route.params.id].img}`;
    },
    show() {
      return localStorage.getItem('outil') === 'boussole'
    },
  },
  mounted() {
    setTimeout(() => {
      this.$refs.audio.pause();
    }, 1000);
  },
  methods: {
    map() {
      saveMap.save();
    },
  }
};
</script>


