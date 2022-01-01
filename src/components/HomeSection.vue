<template>
  <section id="hero">
    <v-parallax dark height="750" class="parallax" id="parallax">
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col
              cols="12"
              md="5"
              xl="4"
              class="
                cardH
                rounded-tl-xl rounded-br-xl
                d-flex
                flex-column
                justify-space-between
              "
            >
              <h1 class="headline my-10">
                Somos una empresa con más de 25 años <br />
                de trayectoria en servicios de fumigaciones y desinfecciones.
              </h1>
              <v-btn
                outlined
                dark
                @click="$vuetify.goTo('#features')"
                class="mt-5 rounded-tl-xl rounded-br-xl py-7 cardBtn"
              >
                En acción!
                <v-icon class="ml-2">mdi-arrow-down</v-icon>
              </v-btn>
            </v-col>
            <v-col cols="12" md="6" xl="4" class="hidden-sm-and-down"> </v-col>
          </v-row>
        </v-col>
      </v-row>
      <div class="svg-border-waves">
        <v-img src="../assets/img/borderWaves.svg" />
      </div>
    </v-parallax>

    <v-container fluid id="features" class="mt-9">
      <h2 class="font-weight-bold display-2 text-center mb-5 text--primary">
        Sobre nosotros!
      </h2>

      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="space-around">
            <v-col
              cols="12"
              sm="4"
              class="text-center"
              v-for="(feature, i) in features"
              :key="i"
            >
              <v-hover v-slot:default="{ hover }" class="glassCard">
                <v-card
                  class="card"
                  shaped
                  :elevation="hover ? 10 : 4"
                  :class="{ up: hover }"
                >
                  <v-img
                    :src="feature.img"
                    max-width="100px"
                    class="d-block ml-auto mr-auto"
                    :class="{ 'zoom-efect': hover }"
                  ></v-img>
                  <h1 class="font-weight-regular">{{ feature.title }}</h1>
                  <h4 class="font-weight-regular subtitle-1">
                    {{ feature.text }}
                  </h4>
                </v-card>
              </v-hover>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <v-dialog v-model="dialog" max-width="640px">
      <v-card>
        <youtube
          :video-id="videoId"
          @ready="ready"
          @playing="playing"
        ></youtube>
      </v-card>
    </v-dialog>
    <div class="svg-border-waves">
      <img src="~@/assets/img/wave2.svg" />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      videoId: "2WoaRMbetPw",
      features: [
        {
          img: require("../assets/imgs/buque.svg"),
          title: "Control integral",
          text: "de plagas en Buques, Casillajes, barcazas y bodegas vacías. ",
        },
        {
          img: require("../assets/imgs/edificio.svg"),
          title: "Control por abono",
          text: "en Consorcios, industrias e instituciones.",
        },
        {
          img: require("../assets/imgs/plaga.svg"),
          title: "Control de roedores",
          text: "mediante monitoreo de estaciones.",
        },
        {
          img: require("../assets/imgs/fumigador.svg"),
          title: "Desinfecciones, sanitizaciones y desinsectaciones",
          text: "por punteo y aspersión según el área o el tipo de plaga.",
        },
        {
          img: require("../assets/imgs/limpieza.png"),
          title: "Limpieza de tanques de agua",
          text: "y realización de análisis bacteriológico y fisicoquímico.",
        },
      ],
    };
  },
  watch: {
    dialog(value) {
      if (!value) {
        this.pause();
      }
    },
  },
  methods: {
    ready(event) {
      this.player = event.target;
    },
    playing(event) {},
    change() {
      this.videoId = "another video id";
    },
    stop() {
      this.player.stopVideo();
    },
    pause() {
      this.player.pauseVideo();
    },
  },
};
</script>

<style lang="scss">
.cardBtn {
  width: 50%;
  height: auto;
}
.cardH {
  background: rgba(117, 123, 181, 0.45);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(3.5px);
  -webkit-backdrop-filter: blur(4.5px);
  border: 1px solid rgba(255, 255, 255, 0.18);
}
</style>

<style lang="scss">
.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 6rem;
  width: 100%;
  overflow: hidden;
  rotate: 34deg;
}

#hero {
  z-index: 0;
}
.svg-border-waves img {
  position: absolute;
  bottom: none;
  left: 0;
  width: 100%;
  margin-bottom: -2px;
  z-index: -1;
}
.glassCard {
  background: rgba(117, 123, 181, 0.45) !important;
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37) !important;
  backdrop-filter: blur(3.5px) !important;
  -webkit-backdrop-filter: blur(4.5px) !important;
  border: 1px solid rgba(255, 255, 255, 0.18) !important;
}
.card {
  min-height: 300px;
  padding: 10px;
  transition: 0.5s ease-out;
}

.card .v-image {
  margin-bottom: 15px;
  transition: 0.75s;
}

.card h1 {
  margin-bottom: 10px;
}

.zoom-efect {
  transform: scale(1.1);
}

.up {
  transform: translateY(-20px);
  transition: 0.5s ease-out;
}
</style>

<style>
section {
  position: relative;
}
.trabajos {
  text-shadow: -3px 3px 1px #2196f3;
  color: rgb(217 235 255);
}
.trabajosS {
  background: #2196f3;
  color: rgb(217 235 255);
  border-radius: 2px;
}
.parallax {
  border: none !important;
  border-inline-style: inherit;
}
#parallax {
  border: none !important;
  border-style: none !important;
}
</style>
