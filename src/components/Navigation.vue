<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
      dark
      src="../assets/imgs/fumiVector.svg"
    >
      <v-list>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="deep-orange--text text--draken-4"
              >Paraná</v-list-item-title
            >
            <v-list-item-subtitle class="blue--text text--draken-4"
              >Fumigaciones</v-list-item-subtitle
            >
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider />

      <v-list dense>
        <v-list-item
          v-for="([icon, text, link], i) in items"
          :key="i"
          link
          @click="$vuetify.goTo(link)"
        >
          <v-list-item-icon class="justify-center">
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{
              text
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      :color="color"
      :flat="flat"
      dark
      class="px-0"
      :class="{ expand: flat }"
    >
      <v-toolbar-title>
        <h1
          class="navT deep-orange--text text--draken-4 font-weight-bold text-h5"
        >
          Paraná
          <span class="navS blue--text text--draken-4 font-weight-bold text-h6"
            >Fumigaciones</span
          >
        </h1>
      </v-toolbar-title>
      <v-spacer />
      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="mr-4  deep-orange--text text--draken-4"
        v-if="isXs"
      />
      <div v-else>
        <v-btn rounded text @click="$vuetify.goTo('#hero')">
          <span class="mr-2 deep-orange--text text--draken-4">Inicio</span>
        </v-btn>
        <v-btn rounded text @click="$vuetify.goTo('#features')">
          <span class="mr-2 deep-orange--text text--draken-4">Nosotros</span>
        </v-btn>
        <v-btn rounded text @click="$vuetify.goTo('#contact')">
          <span class="deep-orange--text text--draken-4">Contacto</span>
        </v-btn>
      </div>
    </v-app-bar>
  </div>
</template>
<style scoped>
.v-toolbar {
  transition: 0.6s;
}

.expand {
  height: 800px !important;
  padding-top: 10px;
  display: none;
}

@media screen and (max-width: 768px) {
  .navT {
    display: none;
  }
}
</style>

<script>
export default {
  data: () => ({
    drawer: null,
    isXs: false,
    items: [
      ["mdi-home-outline", "Inicio", "#hero"],
      ["mdi-information-outline", "Nosotros", "#features"],
      ["mdi-email-outline", "Contacto", "#contact"],
    ],
  }),
  props: {
    color: String,
    flat: Boolean,
  },
  methods: {
    onResize() {
      this.isXs = window.innerWidth < 850;
    },
  },

  watch: {
    isXs(value) {
      if (!value) {
        if (this.drawer) {
          this.drawer = false;
        }
      }
    },
  },
  mounted() {
    this.onResize();
    window.addEventListener("resize", this.onResize, { passive: true });
  },
};
</script>
