<template color="#F5F5F5">
  <v-app color="#5CBBF6">
    <v-snackbar
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
    </v-snackbar>

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
      snackbar1: false,
      snackbar2: false,
      numCitas: "",
      numCitasAnterior: "",
      text: `Nueva cita agregada`,
    };
  },
  mounted() {
    this.actualizarVet(); // Ejecuta la función una vez cuando se carga el componente
    setInterval(this.actualizarVet, 5000); // Ejecuta la función cada 5 segundos
    setInterval(this.actualizarVet, 10000);
  },

  methods: {
    actualizarVet() {
      axios
        .get("http://localhost/xampp/axios/api/veterinario.php", {})
        .then((response) => {
          this.numCitasAnterior = this.numCitas;
          this.numCitas = response.data.num_citas;
          // console.log("Notificacion", this.numCitas);
          if (
            this.numCitas === this.numCitasAnterior ||
            this.numCitas <= this.numCitasAnterior
          ) {
            console.log("hola");
          } else {
            console.log("XD");
            this.snackbar = true;
          }
          // this.numCitas = this.numCitasAnterior;
        })
        .catch((error) => {
          console.error(error);
          //this.snackbar2 = true;
        });
    },
  },
};
</script>



<style></style>
