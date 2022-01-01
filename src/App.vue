<template>
  <v-app>
    <navigation :color="color" />
    <v-main class="pt-0">
      <home />
      <about />
      <contact class="pt-9" />
    </v-main>
    <v-scale-transition>
      <v-btn
        fab
        v-show="fab"
        v-scroll="onScroll"
        dark
        fixed
        bottom
        right
        @click="toTop"
        
      >
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-scale-transition>
    <foote />
  </v-app>
</template>

<style scoped>
.v-main {
  background-image: url(../src/assets/imgs/fumigando2K.jpg);
  image-rendering: auto;
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
}
</style>

<script>
import navigation from "./components/Navigation";
import foote from "./components/Footer";
import home from "./components/HomeSection";
import about from "./components/AboutSection";
import contact from "./components/ContactSection";

export default {
  name: "App",

  components: {
    navigation,
    foote,
    home,
    about,
    contact,
  },
    

  data: () => ({
    fab: null,
    color: "rgba(117, 123, 181, 0.45)",
    flat: null,
  }),

  created() {
    const top = window.pageYOffset || 0;
    if (top <= 60) {
      this.color = "transparent";
      this.flat = true;
    }
  },

  watch: {
    fab(value) {
      if (value) {
        this.color = "rgba(117, 123, 181, 0.50)";
        this.flat = false;
      } else {
        this.color = "transparent";
        this.flat = true;
      }
    },
  },

  methods: {
    onScroll(e) {
      if (typeof window === "undefined") return;
      const top = window.pageYOffset || e.target.scrollTop || 0;
      this.fab = top > 60;
    },
    toTop() {
      this.$vuetify.goTo(0);
    },
  },
};
</script>