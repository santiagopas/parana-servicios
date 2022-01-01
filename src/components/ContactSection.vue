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
              <a
                class="button-icon"
                target="_blank"
                href="https://wa.me/3416546913"
              >
                <v-img
                  src="(../src/assets/imgs/whatsapp.svg)"
                  alt="Número de teléfono / Phone number"
              ></v-img></a>
            </v-col>
            <v-col cols="12" sm="7">
              <v-form>
                <form
                  action="https://formspree.io/f/mrgralep"
                  method="POST"
                  id="form"
                  class="form"
                >
                  <v-text-field required label="Nombre Completo" name="name">
                    <label for="name"
                      >Nombre Completo
                      <input
                        type="text"
                        name="name"
                        id="name"
                        placeholder="Ingresa tu nombre"
                        required
                      />
                    </label>
                  </v-text-field>
                  <v-text-field
                    required
                    label="Correo electrónico"
                    name="email"
                  >
                    <label for="email"
                      >Correo electrónico
                      <input
                        type="email"
                        name="email"
                        id="email"
                        placeholder="Ingresa tu E-Mail"
                        required
                      />
                    </label>
                  </v-text-field>
                  <v-text-field required label="Mensaje" name="message">
                    <label for="message"
                      >Mensaje
                      <textarea
                        name="message"
                        id="message"
                        cols="30"
                        rows="10"
                        required
                      ></textarea>
                    </label>
                  </v-text-field>
                  <div class="btn">
                    <v-btn
                      id="my-form-button"
                      class="button"
                      type="submit"
                      rounded @click="submit"
                      >Enviar Mensaje</v-btn
                    >
                  </div>
                </form>
              </v-form>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <div class="svg-border-waves text-white mt-9">
      <v-img src="~@/assets/img/borderWavesBlue.svg" />
    </div>
  </section>
</template>

<script>
const $form = document.querySelector("#form");

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
    this.reset(
      swal(
        "Mensaje enviado!",
        "👷‍♂️ Nos contactaremos lo antes posible.",
        "success"
      )
    );
    swal(
      "Mensaje enviado!",
      "👷‍♂️ Nos contactaremos lo antes posible.",
      "success"
    );
  } else {
    swal(
      "Vuelve a intentarlo!",
      "Algo salió mal, recarga la página y envia nuevamente el mensaje.",
      "error"
    );
  }
}
</script>
<script>
export default {
  data: () => ({
    icons: ["fa-facebook", "fa-twitter", "fa-linkedin", "fa-instagram"]
  }),
};
</script>
