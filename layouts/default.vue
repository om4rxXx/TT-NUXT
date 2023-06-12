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
      <v-dialog v-model="dialogconect" persistent max-width="400">
        <v-card rounded="xl" style="" dark color="#FF5252">
          <v-card-title class="d-flex justify-center text-h5">
            No hay conexión con el servidor
          </v-card-title>
          <div class="d-flex justify-center py-10">
            <v-icon size="60">mdi-connection</v-icon>
          </div>
          <v-card-text>
            se perdio la conexion con el servidor, checa la conexion a internet
            y vuelve a intentarlo
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn text @click="salir">salir</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
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
      dialogconect: false,
      numCitas: "",
      numCitasAnterior: "",
      text: `Nueva cita agregada`,
    };
  },
  mounted() {
    this.actualizarVet(); // Ejecuta la función una vez cuando se carga el componente
    setInterval(this.actualizarVet, 5000); // Ejecuta la función cada 5 segundos
    setInterval(this.actualizarVet, 10000);
    this.testConnection();
    setInterval(this.testConnection, 10000);
  },

  methods: {
    salir() {
      document.cookie =
        "Veterinario=" + "=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
      this.dialogconect = false;
      this.$router.push("/");
      //this.$cookies.set("username", "gowtham");
    },
    testConnection() {
      axios
        .get("http://localhost/xampp/axios/api/pruebita.php")
        .then((response) => {
          // Si la conexión es exitosa, la respuesta será el JSON codificado
          const result = response.data;
          // Verificar si hay conexión exitosa
          if (result === 1) {
            console.log("Conexión exitosa");
            this.dialogconect = false;
          } else {
            console.log("No hay conexión");
            this.dialogconect = true;
          }
        })
        .catch((error) => {
          console.log("Error al realizar la solicitud:", error);
        });
    },
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
