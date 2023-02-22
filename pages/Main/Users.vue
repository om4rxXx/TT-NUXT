<template>
  <v-app>
    <nav-l></nav-l>
    <v-container class="pt-12 px-15">
      <v-card flat>
        <v-toolbar color="#5CBBF6" class="mx-3 my-1 rounded-pill" flat>
          <v-avatar class="px-3">
            <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
          </v-avatar>

          <v-toolbar-title class="ml-3 white--text">Mr Can</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-col md="4" sm="4" lg="4">
            <v-text-field
              class="pt-8"
              v-model="search"
              label="Buscar"
              solo
              append-icon="mdi-magnify"
              rounded
            ></v-text-field>
          </v-col>
        </v-toolbar>
      </v-card>
      <div class="pt-12">
        <v-card elevation="14" class="rounded-xl">
          <v-data-table
            :headers="headers"
            :items="desserts"
            item-key="name"
            class="elevation-1"
            :search="search"
            elevation="14"
            @click="XD"
          >
            <template v-slot:[`item.status`]="{ item }">
              <v-dialog v-model="dialog" width="500">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                    small
                    rounded
                    :color="getColor(item.status)"
                    dark
                    >{{ item.status }}</v-btn
                  >
                </template>
                <v-card class="rounded-xl">
                  <div class="d-flex justify-center pt-7">
                    <v-icon large color="yellow" dark> mdi-alert </v-icon>
                  </div>
                  <div class="d-flex justify-center pt-7">
                    <h3>Aceptación de usuario</h3>
                  </div>
                  <div class="d-flex justify-center pt-7">
                    ¿Está seguro que desea aceptar al usuario?
                  </div>
                  <v-card-actions class="d-flex justify-center">
                    <div class="d-flex justify-center">
                      <v-btn
                        height="50"
                        class="btn-center white--text rounded-xl ma-6"
                        depressed
                        color="#34A853"
                        :loading="loading"
                        @click="editarUser"
                      >
                        ACEPTAR
                      </v-btn>
                      <v-btn
                        height="50"
                        class="btn-center white--text rounded-xl ma-6"
                        depressed
                        color="#FF5252"
                        :loading="loading"
                      >
                        Cancelar
                      </v-btn>
                    </div>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </template>
            <template v-slot:[`item.mascotas`]="{ item }">
              <v-chip class="ma-2" color="#5CBBF6" dark>
                {{ item.mascotas }}
              </v-chip>
            </template>
            <template v-slot:[`item.baja`]>
              <v-dialog v-model="dialog" width="500">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                    class="ma-2"
                    text
                    icon
                    color="red lighten-2"
                  >
                    <v-icon>mdi-delete</v-icon>
                  </v-btn>
                </template>
                <v-card class="rounded-xl">
                  <div class="d-flex justify-center pt-7">
                    <v-icon large color="yellow" dark> mdi-alert </v-icon>
                  </div>
                  <div class="d-flex justify-center pt-7">
                    <h3>Dar de baja usuario</h3>
                  </div>
                  <div class="d-flex justify-center pt-7">
                    ¿Está seguro que desea dar de baja al usuario?
                  </div>
                  <v-card-actions class="d-flex justify-center">
                    <div class="d-flex justify-center">
                      <v-btn
                        height="50"
                        class="btn-center white--text rounded-xl ma-6"
                        depressed
                        color="#34A853"
                        :loading="loading"
                        @click="editarUser"
                      >
                        ACEPTAR
                      </v-btn>
                      <v-btn
                        height="50"
                        class="btn-center white--text rounded-xl ma-6"
                        depressed
                        color="#FF5252"
                        :loading="loading"
                      >
                        Cancelar
                      </v-btn>
                    </div>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </template>
          </v-data-table>
        </v-card>
      </div>
    </v-container>
  </v-app>
</template>

<script>
import NavL from "~/components/NavL.vue";
import NavR from "~/components/NavR.vue";

export default {
  components: {
    NavL,
    NavR,
  },

  data() {
    return {
      search: "",

      headers: [
        {
          text: "Nombre",
          align: "center",

          value: "name",
        },
        { text: "Estado de Solicitud", align: "center", value: "status" },
        { text: "Mascotas", value: "mascotas", align: "center" },
        { text: "Dar de baja", value: "baja", align: "center" },
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          status: "Aceptado",
          mascotas: ("tsao", "sd"),
          baja: 24,
        },

        {
          name: "Lollipop",
          status: "Pendiente",
          mascotas: "juan",
          baja: 54,
        },
        {
          name: "Honeycomb",
          status: "Rechazado",
          mascotas: "Peso pluma",
          baja: 55,
        },
        {
          name: "Donut",
          status: "Aceptado",
          mascotas: "junior h",
          baja: 55,
        },
        {
          name: "KitKat",
          status: "Aceptado",
          mascotas: "junior h",
          baja: 55,
        },
      ],
    };
  },
  methods: {
    getColor(calories) {
      if (calories == "Rechazado") return "red";
      else if (calories == "Pendiente") return "orange";
      else return "green";
    },
    filterOnlyCapsText(value, search, item) {
      return (
        value != null &&
        search != null &&
        typeof value === "string" &&
        value.toString().toLocaleUpperCase().indexOf(search) !== -1
      );
    },
    XD() {
      this.$router.push("https://v2.vuetifyjs.com/en/api/v-data-table/#props");
    },
  },
};
</script>

<style></style>
