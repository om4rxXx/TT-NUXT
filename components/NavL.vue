<template>
  <v-navigation-drawer app elevation="14">
    <v-list-item link to="/XD/Perfil">
      <v-list-item-content>
        <v-list-item-title class="text-h6">
          <template v-if="veterinario.foto_veterinario">
            <v-avatar>
              <img
                :src="'data:image/png;base64,' + veterinario.foto_veterinario"
                alt="John"
              />
            </v-avatar>
          </template>
          <template v-else
            ><v-avatar
              ><img src="~/assets/images/logito.png" alt="John"
            /></v-avatar>
          </template>
          {{ veterinario.nombre_veterinario }}
          {{ veterinario.apellido_veterinario }}
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-divider></v-divider>

    <v-list dense nav active-class="deep-purple--text text--accent-4">
      <v-list-item link to="/XD/Principal">
        <v-list-item-icon>
          <v-icon>mdi-calendar-clock-outline</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title
            ><h3>
              Citas<v-badge
                inline
                color="#5C0FD9"
                dark
                :content="veterinario.num_citas"
              ></v-badge></h3
          ></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item link to="/XD/Users">
        <v-list-item-icon>
          <v-icon>mdi-account-supervisor-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title><h3>Usuarios</h3></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <template v-slot:append>
      <v-list-item @click="eliminarCookie">
        <v-list-item-icon>
          <v-icon>mdi-logout</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Cerrar sesión</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </template>
  </v-navigation-drawer>
</template>

<script lang="ts">
import axios from "axios";
import moment from "moment";
export default {
  name: "NavR",
  data() {
    return {
      veterinario: [],
    };
  },
  mounted() {
    this.actualizarVet(); // Ejecuta la función una vez cuando se carga el componente
    setInterval(this.actualizarVet, 1000); // Ejecuta la función cada 5 segundos
    axios
      .get("http://localhost:8080/xampp/axios/api/veterinario.php", {})
      .then((response) => {
        this.veterinario = response.data;
        console.log(response.data);
      })
      .catch((error) => {
        console.error(error);
      });
  },
  methods: {
    eliminarCookie() {
      document.cookie =
        "Veterinario=" + "=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
      this.$router.push("/");
      //this.$cookies.set("username", "gowtham");
    },
    // traer datos de consulta
    actualizarVet() {
      axios
        .get("http://localhost:8080/xampp/axios/api/veterinario.php", {})
        .then((response) => {
          this.veterinario = response.data;
          console.log(response.data);
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>



<style >
.v-progress-circular {
  margin: 3rem;
}
.purple-gradient {
  background-color: #1fd1f9;
  background-image: linear-gradient(to right, #5ce1e6, #cb6ce6, #ff66c4);
  transition: all 0.3s ease;
  color: white;
  transition: all 0.3s ease-out;
}
</style>
