<template color="#F5F5F5">
  <v-app color="#5CBBF6">
    <!--<v-snackbar
      v-model="snackbar"
      :multi-line="multiLine"
      shaped
      left
      color="#5C0FD9"
      dark
    >
      <h3>{{ text }}</h3>

      <template v-slot:action="{ attrs }">
        <v-btn
          v-bind="attrs"
          @click="snackbar = false"
          class="ma-2"
          text
          icon
          color="white"
        >
          <v-icon large>mdi-close-circle</v-icon>
        </v-btn>
      </template>
    </v-snackbar>-->
    <v-main color="#5CBBF6">
      <v-container color="#F5F5F5">
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import axios from "axios";
import moment from "moment";
export default {
  name: "NavR",
  data() {
    return {
      veterinario: [],
      citas: "",
      anterior: "",
      multiLine: true,
      snackbar: false,
      text: `Nueva cita agregada`,
    };
  },
  mounted() {
    this.actualizarVet(); // Ejecuta la función una vez cuando se carga el componente
    setInterval(this.actualizarVet, 5000); // Ejecuta la función cada 5 segundos
  },

  methods: {
    // traer datos de consulta
    actualizarVet() {
      axios
        .get("http://localhost:8080/xampp/axios/api/veterinario.php", {})
        .then((response) => {
          const numCitas = response.data.num_citas;

          // Actualiza el valor de this.citas sólo si ha habido un cambio
          if (numCitas !== this.citas) {
            console.log("SDSDS", numCitas);
            this.anterior = this.citas;
            this.citas = numCitas;

            // Verifica si ha habido un cambio
            if (this.anterior === undefined || this.citas > this.anterior) {
              console.log("Hola");
              this.snackbar = true;
            }
          }
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>



<style></style>
