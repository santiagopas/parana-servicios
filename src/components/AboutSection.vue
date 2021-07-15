@import "../assets/imgs/v"
<template>
  <section id="about">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row align="center" justify="center">
            <v-col cols="12" md="7">
              <h1 class="font-weight-light display-2">Sobre</h1>
              <h1 class="font-weight-bold display-1 mb-3">
                Nosotros!
              </h1>
              <v-row>
                <v-col cols="12" class="d-flex align-center">
                  <v-img
                    src="../assets/imgs/historia.svg"
                    max-width="60px"
                    class="mr-4"
                  />
                  <p class="text-justify">
                    Desde 1996 nos enfocamos en el manejo integral de plagas en
                    instalaciones portuarias, buques, industrias, instituciones
                    y consorcios.
                  </p>
                </v-col>
                <v-col cols="12" class="d-flex align-center">
                  <v-img
                    src="../assets/imgs/pesticida.svg"
                    max-width="60px"
                    class="mr-4"
                  />
                  <p class="text-left">
                    Somos especialistas en la aplicación de una gran variedad de
                    plaguicidas y desinfectantes. Este conocimiento junto a las
                    herramientas adecuadas, nos permite brindar diversos
                    servicios que simplifican la tarea del cliente a la hora de
                    contratar un proveedor capaz de resolver distintas demandas.
                  </p>
                </v-col>
                <v-col cols="12" class="d-flex align-center">
                  <v-img
                    src="../assets/imgs/control.svg"
                    max-width="60px"
                    class="mr-4"
                  />
                  <p class="text-justify">
                    Un exhaustivo control de plagas es imprescindible para la
                    salud pública. La proliferación de colonias de insectos y
                    roedores, pueden provocar graves problemas físicos y
                    económicos, ya que además de ser una fuente de enfermedades,
                    las plagas pueden causar grandes destrozos materiales.
                  </p>
                </v-col>
              </v-row>
            </v-col>
            <v-col cols="12" md="5" class="d-none d-md-flex">
              <v-img
                src="../assets/imgs/working.svg"
                class="d-block ml-auto mr-auto"
                max-width="400px"
              />
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </section>
</template>

<style scoped>

#about {
  background-color: #f4f7f5;
}
</style>
