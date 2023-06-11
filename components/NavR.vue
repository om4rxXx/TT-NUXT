<template>
  <v-navigation-drawer permanent app right>
    <template v-if="veterinario.foto_veterinario">
      <v-img
        height="200"
        :src="'data:image/png;base64,' + veterinario.foto_veterinario"
      ></v-img>
    </template>
    <template v-else>
      <img src="~/assets/images/logito.png" height="200" alt="John"
    /></template>
    <v-divider class="mx-4"></v-divider>

    <v-list dense nav>
      <v-list-item class="md-4">
        <v-list-item-content>
          <v-list-item-title><h2>Contacto</h2></v-list-item-title>
        </v-list-item-content>
        <v-list-item-icon>
          <v-btn icon to="/XD/Perfil">
            <v-icon>mdi-pencil</v-icon>
          </v-btn>
        </v-list-item-icon>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-account-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Veterinario</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-phone-classic</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title
            >+52 {{ veterinario.telefono_veterinario }}</v-list-item-title
          >
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-email-fast-outline</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{
            veterinario.email_veterinario
          }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title><h2>Información adicional</h2></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-calendar-badge-outline</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title
            >{{ new Date().getDate() }}/{{ new Date().getMonth() + 1 }}/{{
              new Date().getFullYear()
            }}</v-list-item-title
          >
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-account-supervisor-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title
            >{{ veterinario.num_usuarios }} clientes</v-list-item-title
          >
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-map-marker</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title
            ><v-tooltip bottom color="#5CBBF6">
              <template v-slot:activator="{ on, attrs }">
                <span v-bind="attrs" v-on="on"
                  >{{ veterinario.ciudad_veterinario }},
                  {{ veterinario.estado_veterinario }},
                  {{ veterinario.calle_veterinario }}
                  {{ veterinario.num_ext_veterinario }}</span
                >
              </template>
              <span
                >{{ veterinario.ciudad_veterinario }},
                {{ veterinario.estado_veterinario }},
                {{ veterinario.calle_veterinario }}
                {{ veterinario.num_ext_veterinario }}</span
              >
            </v-tooltip></v-list-item-title
          >
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-account-supervisor-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Administrador</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
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
      citas: "",
      anterior: "",
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
        .get("http://localhost/xampp/axios/api/veterinario.php", {})
        .then((response) => {
          this.veterinario = response.data;
          console.log(response.data);
          this.anterior = this.citas;
          this.citas = response.data.num_citas;

          if (this.citas > this.anterior) {
            console.log("Hola");
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
