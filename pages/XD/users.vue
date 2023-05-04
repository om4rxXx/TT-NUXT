<template>
  <v-app>
    <nav-l></nav-l>

    <v-container class="pt-12">
      <v-col cols="12">
        <v-card flat>
          <v-toolbar color="#5CBBF6" class="mx-3 my-1 rounded-pill" flat>
            <v-avatar class="px-3">
              <img src="~/assets/images/logito.png" alt="John" />
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
              :items="usuarios"
              item-key="name"
              class="elevation-1"
              :search="search"
              elevation="14"
            >
              <template v-slot:[`item.usuario`]="{ item }">
                <v-avatar color="blue-grey lighten-4">
                  <template v-if="item.foto_usuario">
                    <v-img
                      :src="'data:image/png;base64,' + item.foto_usuario"
                    ></v-img>
                  </template>
                  <template v-else>
                    <v-icon>mdi-account</v-icon>
                  </template>
                </v-avatar>
                <v-btn @click="XD(item.id_usuario)" text small rounded>
                  {{ item.usuario }}
                </v-btn>
              </template>
              <template v-slot:[`item.estatus_usuario`]="{ item }">
                <v-btn
                  small
                  rounded
                  :color="getColor(item.estatus_usuario).color"
                  dark
                  @click="openDialogEditStatus(item.id_usuario, 2)"
                >
                  {{ getColor(item.estatus_usuario).text }}</v-btn
                >
              </template>
              <template v-slot:[`item.num_mascotas`]="{ item }">
                <v-chip class="ma-2" color="#5CBBF6" dark>
                  {{ item.num_mascotas }}
                </v-chip>
              </template>
              <template v-slot:[`item.baja_usuario`]="{ item }">
                <div v-if="item.estatus_usuario != 1">
                  <v-btn
                    class="ma-2"
                    text
                    icon
                    color="red lighten-2"
                    @click="openDialogEliminar(item.id_usuario, 1)"
                  >
                    <v-icon>mdi-delete</v-icon>
                  </v-btn>
                </div>
              </template>
            </v-data-table>
          </v-card>
        </div>
        <!--Dialogsss
        -->
        <v-dialog v-model="dialogEstatus" width="500">
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
                  @click="CambiarEstado"
                >
                  ACEPTAR
                </v-btn>
                <v-btn
                  height="50"
                  class="btn-center white--text rounded-xl ma-6"
                  depressed
                  color="#FF5252"
                  @click="dialogEstatus = false"
                >
                  Cancelar
                </v-btn>
              </div>
            </v-card-actions>
          </v-card>
        </v-dialog>
        <v-dialog v-model="dialogEliminar" width="500">
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
                  @click="CambiarEstado"
                >
                  ACEPTAR
                </v-btn>
                <v-btn
                  height="50"
                  class="btn-center white--text rounded-xl ma-6"
                  depressed
                  color="#FF5252"
                  @click="dialogEliminar = false"
                >
                  Cancelar
                </v-btn>
              </div>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-col>
    </v-container>
  </v-app>
</template>

<script lang="ts">
import NavL from "~/components/NavL.vue";
import NavR from "~/components/NavR.vue";
import axios from "axios";

export default {
  components: {
    NavL,
    NavR,
  },

  data() {
    return {
      search: "",
      dialogEstatus: false,
      dialogEliminar: false,
      idUsuario: 0,
      estatus: 0,

      headers: [
        {
          text: "Nombre",

          value: "usuario",
        },
        {
          text: "Estado de Solicitud",
          align: "center",
          value: "estatus_usuario",
        },

        {
          text: "Num Mascotas",
          value: "num_mascotas",
          align: "center",
        },
        { text: "Dar de baja", value: "baja_usuario", align: "center" },
      ],

      usuarios: [],
    };
  },

  async mounted() {
    try {
      const response = await axios.get(
        "http://localhost:8080/xampp/axios/api/listar_usersYmascotas.php"
      );
      this.usuarios = response.data;
      console.log(this.usuarios);

      // Actualizar la lista de usuarios y mascotas cada 5 segundos
      setInterval(async () => {
        const response = await axios.get(
          "http://localhost:8080/xampp/axios/api/listar_usersYmascotas.php"
        );
        this.usuarios = response.data;
        console.log(this.usuarios);
      }, 5000);
    } catch (error) {
      console.log(error);
    }
    const existe = this.checkCookie();
    if (existe) {
      console.log("La cookie existe");
    } else {
      this.$router.push("/");
    }
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
    getColor(calories: string) {
      if (calories == "1") return { color: "red", text: "Eliminado" };
      else if (calories == "0") return { color: "orange", text: "Pendiente" };
      else return { color: "success", text: "Aceptado" };
    },
    filterOnlyCapsText(
      value: { toString: () => string } | null,
      search: string | null,
      item: any
    ) {
      return (
        value != null &&
        search != null &&
        typeof value === "string" &&
        value.toString().toLocaleUpperCase().indexOf(search) !== -1
      );
    },
    CambiarEstado(id: string, number: number) {
      axios
        .get("http://localhost:8080/xampp/axios/api/editarstatus.php", {
          params: {
            id_usuario: this.idUsuario, // suponiendo que tienes una variable 'id' en tu componente Vue
            numero: this.estatus, // suponiendo que tienes una variable 'numero' en tu componente Vue
          },
        })
        .then((response) => {
          console.log(response.data);
          this.dialogEstatus = false;
          this.dialogEliminar = false;
          // window.location.reload();
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    openDialogEditStatus(id_usuario: number, number: number) {
      this.dialogEstatus = true;
      this.idUsuario = id_usuario;
      this.estatus = number;
    },
    openDialogEliminar(id_usuario: number, number: number) {
      this.dialogEliminar = true;
      this.idUsuario = id_usuario;
      this.estatus = number;
    },
    XD(id: string) {
      this.$router.push(id + "/perfilCliente");
    },
  },
};
</script>

<style></style>
