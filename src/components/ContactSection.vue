<template>
  <section class="pb-8" id="contact">
    <v-container fluid>
      <v-row align="center" justify="center">
        <v-col cols="10">
          <v-row justify="center">
            <v-col cols="12" sm="5">
              <h1 class="font-weight-bold display-1">Escribinos</h1>
              <h3 class="font-weight-light mt-3">
                Estaremos contactandote a la brevedad.
              </h3>
              <h3 class="font-weight-light mt-3">
                Teléfono: +54 (341) 153-123234
              </h3>
            </v-col>
            <!-- aca va el v form -->
            <v-col cols="12" sm="7">
              <!-- modify this form HTML and place wherever you want your form -->
              <v-form>
                <form
                  id="my-form"
                  action="https://formspree.io/f/mrgralep"
                  method="POST"
                >
                  <v-text-field
                    v-model="name"
                    :rules="nameRules"
                    label="Nombre"
                    type="text"
                    name="name"
                    required
                  ></v-text-field>

                  <v-text-field
                    v-model="email"
                    :rules="emailRules"
                    label="E-mail"
                    type="email"
                    name="email"
                    required
                  ></v-text-field>

                  <v-textarea
                    v-model="textArea"
                    :rules="textAreaRules"
                    label="Mensaje"
                    type="text"
                    name="message"
                    required
                  />
                  <div class="cajaBoton">
                    <v-btn id="my-form-button"> Enviar </v-btn>
                  </div>
                </form>
              </v-form>
              <!-- Place this script at the end of the body tag -->
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves text-white">
      <v-img src="~@/assets/img/borderWavesBlue.svg" />
    </div>
    <v-snackbar
      v-model="snackbar.enabled"
      timeout="3000"
      right
      top
      :color="snackbar.color"
    >
      {{ snackbar.text }}

      <template v-slot:action="{ attrs }">
        <v-btn text v-bind="attrs" @click="snackbar.enabled = false">
          Fecha
        </v-btn>
      </template>
    </v-snackbar>
  </section>
</template>


<script src="https://unpkg.com/sweetalert/dist/sweetalert.min.js">
const $form = document.querySelector("#my-form");

$form.addEventListener("submit", handleSubmit);

async function handleSubmit(event) {
  event.preventDefault();
  const form = new FormData(this);
  const response = await fetch(this.action, {
    method: this.method,
    body: form,
    headers: {
      Accept: "application/json",
    },
  });
  if (response.ok) {
    this.reset();
    swal("Gracias por contactarme", "te escribiré pronto 😃", "success");
  }
}
</script>
<style>
.cajaBoton {
  display: flex;
  justify-content: center;
  align-items: center;
}
#my-form-button{
  background: linear-gradient(to top, #f12711, #f5af19);
  width: 60%;
  color: #f4f7f5;
}
</style>

<style scoped>
#contact {
  background-color: #f4f7f5;
}

.svg-border-waves .v-image {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3rem;
  width: 100%;
  overflow: hidden;
}
</style>

<script>
export default {
  data: () => ({
    icons: ["fa-facebook", "fa-twitter", "fa-linkedin", "fa-instagram"],
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "El campo nombre es obligatorio",
      (v) =>
        (v && v.length >= 6) || "El nombre precisa tener 6 o más caracterers",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "El campo nombre es obligatorio",
      (v) => /.+@.+\..+/.test(v) || "El E-mail precisa ser válido",
    ],
    textArea: "",
    textAreaRules: [
      (v) => !!v || "El campo texto es obligatorio",
      (v) => (v && v.length >= 10) || "Mínimo de 10 caracteres",
    ],
    lazy: false,
    snackbar: {
      enabled: false,
      text: "",
      color: "",
    },
  }),
};
</script>
