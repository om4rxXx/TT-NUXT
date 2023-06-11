<template>
  <v-app>
    <nav-l></nav-l>
    <v-container class="pt-12">
      <v-card flat>
        <v-toolbar color="#5CBBF6" class="rounded-pill" app>
          <v-avatar color="blue-grey lighten-4">
            <template v-if="mascota.foto_usuario">
              <v-img :src="mascota.foto_usuario"></v-img>
            </template>
            <template v-else>
              <v-icon>mdi-account</v-icon>
            </template>
          </v-avatar>

          <v-toolbar-title class="ml-3 white--text">{{
            mascota.nombre_usuario + " " + mascota.apellido_usuario
          }}</v-toolbar-title>
        </v-toolbar>
      </v-card>
      <v-row>
        <v-col sm="8" md="8" lg="8" xl="8">
          <v-card class="rounded-xl" elevation="14" height="235">
            <v-row class="ma-5 py-12"
              ><v-col sm="3" md="3">
                <v-avatar size="90" color="blue-grey lighten-4">
                  <template v-if="mascota.foto_mascota">
                    <img :src="mascota.foto_mascota" alt="John"
                  /></template>
                  <template v-else>
                    <v-icon>mdi-paw</v-icon>
                  </template>
                </v-avatar></v-col
              >
              <v-col sm="4" md="4">
                <v-list lines="one" density="compact"
                  ><v-list-item>
                    <v-list-item-content>
                      <v-list-item-title
                        ><h3>
                          {{ mascota.nombre_mascota }}
                        </h3></v-list-item-title
                      >
                    </v-list-item-content>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-content>
                      <v-list-item-title>
                        {{ mascota.especie_mascota }}</v-list-item-title
                      >
                    </v-list-item-content>
                  </v-list-item>
                </v-list></v-col
              ><v-col sm="5" md="5">
                <v-list lines="one" density="compact">
                  <v-list-item>
                    <v-list-item-content>
                      <v-list-item-title
                        >Dueño:
                        {{
                          " " +
                          mascota.nombre_usuario +
                          " " +
                          mascota.apellido_usuario
                        }}</v-list-item-title
                      >
                    </v-list-item-content>
                  </v-list-item>
                </v-list></v-col
              ></v-row
            >
          </v-card>
        </v-col>
        <v-col sm="4" md="4" lg="4">
          <v-card class="rounded-xl mx-auto my-5" elevation="14" height="235">
            <v-card-title>Datos</v-card-title>
            <v-card-text>
              <v-row>
                <v-col sm="8" md="8" lg="8">
                  <v-list lines="one" density="compact" class="pl-5">
                    <p>Nacimiento:</p>
                    <p>Raza:</p>
                    <p>Padecimientos:</p>
                    <p>Sexo:</p>
                  </v-list>
                </v-col>
                <v-col class="d-flex justify-end" sm="4" md="4" lg="4">
                  <v-list lines="one" density="compact" class="pr-3">
                    <p>
                      {{
                        moment(mascota.fecha_nacimiento_mascota)
                          .locale("es")
                          .format("DD/MM/YY")
                      }}
                    </p>
                    <p>{{ mascota.raza_mascota }}</p>
                    <p>
                      <template v-if="mascota.padecimientos_mascota"
                        >{{ mascota.padecimientos_mascota }}
                      </template>
                      <template v-else> Ninguno</template>
                    </p>
                    <p>{{ mascota.sexo_mascota }}</p>
                  </v-list>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <v-card class="mx-auto rounded-xl" elevation="14">
        <v-card-title class="text-center justify-center py-6">
          <h1 class="font-weight-bold text-h2 basil--text">Historial</h1>
        </v-card-title>

        <v-tabs v-model="tab" background-color="#5CBBF6" dark fixed-tabs>
          <v-tab v-for="item in items" :key="item.tab">
            {{ item.tab }}
          </v-tab>
        </v-tabs>

        <v-tabs-items v-model="tab">
          <v-tab-item v-for="item in items" :key="item.tab">
            <v-card flat v-if="item.tab === 'Medica'">
              <v-data-table
                :headers="headers"
                :items="consultaM"
                :items-per-page="5"
                ><template v-slot:item.fecha_cita="{ item }">
                  {{ moment(item.fecha_cita).locale("es").format("DD/MM/YY") }}
                </template></v-data-table
              >
            </v-card>
            <v-card flat v-if="item.tab === 'Vacunacion'">
              <v-data-table
                :headers="headers"
                :items="consultaV"
                :items-per-page="5"
                ><template v-slot:item.fecha_cita="{ item }">
                  {{ moment(item.fecha_cita).locale("es").format("DD/MM/YY") }}
                </template></v-data-table
              >
            </v-card>
          </v-tab-item>
        </v-tabs-items>
        <!-- <v-tabs-items v-if="item === 'Vacunacion'">
          <v-tab-item v-for="(item, index) in consultaV" :key="index">
            <v-card flat>
              <v-card-text>
                <v-data-table
                  :headers="headers"
                  :items="consultaV"
                  :items-per-page="5"
                ></v-data-table>
              </v-card-text>
            </v-card>
          </v-tab-item>
        </v-tabs-items>-->
      </v-card>
    </v-container>
  </v-app>
</template>

<script lang="ts">
import axios from "axios";
import moment from "moment";
export default {
  data() {
    return {
      moment: moment,
      nose: "",
      text: "Lorem ipsum d",

      hoy: moment,
      tab: null,
      items: ["Medica", "Vacunacion"],
      headers: [
        {
          text: "Nombre Producto",
          align: "center",
          sortable: false,
          value: "producto_consulta",
        },
        {
          text: "fecha de aplicacion",
          value: "fecha_cita",
          align: "center",
        },
        {
          text: "Peso(KG)",
          value: "peso_consulta",
          sortable: false,
          align: "center",
        },

        {
          text: "Quien aplico",
          value: "aplico_consulta",
          sortable: false,
          align: "center",
        },
        {
          text: "Observaciones",
          value: "observaciones_consulta",
          sortable: false,
          align: "center",
        },
      ],
      items: [
        { tab: "Medica", content: "Tab 1 Content" },
        { tab: "Vacunacion", content: "Tab 2 Content" },
      ],

      mascota: [],
      consultaV: [],
      consultaM: [],
    };
  },
  mounted() {
    const existe = this.checkCookie();
    if (existe) {
      console.log("La cookie existe");
    } else {
      this.$router.push("/");
    }
    // traer mascota
    console.log(this.$route.params.mascota);
    axios
      .get("http://localhost/xampp/axios/api/traerMascota.php", {
        params: {
          id_mascota: parseInt(this.$route.params.mascota), //ahorita
        },
      })
      .then((response) => {
        this.mascota = response.data;
        console.log(this.$route.params.Clientes);
        console.log(this.mascota);
      })
      .catch((error) => {
        console.error(error);
      });
    //nueva traer consultas VVVVVVVVV
    axios
      .get("http://localhost/xampp/axios/api/HistorialV.php", {
        params: {
          id_mascota: parseInt(this.$route.params.mascota), //ahorita
        },
      })
      .then((response) => {
        this.consultaV = response.data;

        console.log("hshshs", this.items);
      })
      .catch((error) => {
        console.error(error);
      });
    // traer consulta MMMMMMM
    axios
      .get("http://localhost/xampp/axios/api/HistorialC.php", {
        params: {
          id_mascota: parseInt(this.$route.params.mascota), //ahorita
        },
      })
      .then((response) => {
        this.consultaM = response.data;
        console.log(this.$route.params.Clientes);
        console.log(this.consultaM);
      })
      .catch((error) => {
        console.error(error);
      });
  },
  methods: {
    checkCookie() {
      const cookies = document.cookie.split("; ");
      for (let i = 0; i < cookies.length; i++) {
        const cookie = cookies[i].split("=");
        if (cookie[0] === "Veterinario") {
          return true; // La cookie existe
        }
      }
      return false; // La cookie no existe
    },
    XD(item: string) {
      this.nose = item;
      console.log(item);
    },
  },
};
</script>

<style></style>
