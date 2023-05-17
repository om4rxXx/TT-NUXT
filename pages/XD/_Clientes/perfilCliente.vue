<template>
  <v-app>
    <nav-l></nav-l>
    <v-container class="pt-12">
      <v-card flat>
        <v-toolbar color="#5CBBF6" class="rounded-pill" flat>
          <v-avatar color="blue-grey lighten-4">
            <template v-if="usuario.foto_usuario">
              <v-img
                :src="'data:image/png;base64,' + usuario.foto_usuario"
              ></v-img>
            </template>
            <template v-else>
              <v-icon>mdi-account</v-icon>
            </template>
          </v-avatar>

          <v-toolbar-title class="ml-3 white--text">
            {{
              usuario.nombre_usuario + " " + usuario.apellido_usuario
            }}</v-toolbar-title
          >
        </v-toolbar>
      </v-card>
      <v-row>
        <v-col sm="4" md="4" lg="4">
          <v-card
            class="mx-auto my-5 rounded-xl"
            elevation="14"
            max-width="374"
          >
            <template v-if="usuario.foto_usuario">
              <v-img
                height="250"
                :src="'data:image/png;base64,' + usuario.foto_usuario"
              ></v-img>
            </template>
            <template v-else>
              <div class="d-flex justify-center">
                <v-img
                  class="d-flex justify-center"
                  src="https://cdn-icons-png.flaticon.com/512/6073/6073873.png"
                  height="250"
                  width="150"
                >
                </v-img>
              </div>
            </template>

            <v-card-text>
              <v-list dense>
                <v-list-item class="md-4">
                  <v-list-item-content>
                    <v-list-item-title><h2>Contacto</h2></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-account-circle</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>{{
                      usuario.nombre_usuario + " " + usuario.apellido_usuario
                    }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-phone-classic</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>{{
                      usuario.telefono_usuario
                    }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-email-fast-outline</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>{{
                      usuario.email_usuario
                    }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col sm="8" md="8" lg="8">
          <v-card elevation="14" class="rounded-xl mx-auto my-5">
            <v-card-title>Resumen de citas</v-card-title>
            <v-card-text>
              <v-row>
                <v-col sm="8" md="8" lg="8">
                  <v-list
                    ><v-list-item>
                      <v-list-item-icon>
                        <v-icon>mdi-content-cut</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>Estéticas</v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                    <v-list-item>
                      <v-list-item-icon>
                        <v-icon>mdi-medical-bag</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>Médicas</v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                    <v-list-item>
                      <v-list-item-icon>
                        <v-icon>mdi-needle</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>Vacunación</v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list>
                </v-col>
                <v-col class="d-flex justify-center" sm="4" md="4" lg="4">
                  <v-list
                    ><v-list-item>
                      <v-list-item-icon>
                        <v-icon color="white">mdi-account-circle</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>{{
                          citas.Estetica
                        }}</v-list-item-title>
                      </v-list-item-content> </v-list-item
                    ><v-list-item>
                      <v-list-item-icon>
                        <v-icon color="white">mdi-account-circle</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>{{
                          citas.Medica
                        }}</v-list-item-title>
                      </v-list-item-content> </v-list-item
                    ><v-list-item>
                      <v-list-item-icon>
                        <v-icon color="white">mdi-account-circle</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>{{
                          citas.Vacunacion
                        }}</v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <v-row class="px-4 pb-6" justify="space-between">
            <h2>Mascotas</h2>
            <v-dialog v-model="dialogCrear" width="500">
              <template v-slot:activator="{ on, attrs }">
                <v-btn dark color="#5CBBF6" rounded v-bind="attrs" v-on="on">
                  Agregar mascota <v-icon class="ml-5" left> mdi-plus </v-icon>
                </v-btn>
              </template>

              <v-card elevation="14" class="rounded-xl">
                <v-card-title class="text-h5 lighten-2">
                  Nueva mascota
                </v-card-title>
                <div class="d-flex justify-center">
                  <v-form ref="form">
                    <div class="text-center my-1 py-1">
                      <v-text-field
                        v-model="NombreM"
                        label="Nombre"
                        outlined
                        dense
                        :rules="[rules.required]"
                        color="primary"
                      ></v-text-field>
                      <v-select
                        :items="items"
                        label="Sexo"
                        @input="onSexoSelect"
                        v-model="sexo"
                        outlined
                        :rules="[rules.required]"
                      ></v-select>
                      <v-text-field
                        v-model="Color"
                        label="Color"
                        outlined
                        dense
                        color="primary"
                        :rules="[rules.required]"
                      ></v-text-field>
                      <v-text-field
                        v-model="Especie"
                        label="Especie"
                        outlined
                        dense
                        color="primary"
                        :rules="[rules.required]"
                      ></v-text-field>
                      <v-text-field
                        v-model="Raza"
                        label="Raza"
                        outlined
                        dense
                        color="primary"
                        :rules="[rules.required]"
                      ></v-text-field>
                      <!--<v-text-field
            v-model="Sexo"
            label="Sexo (Macho o Hembra)"
            outlined
            dense
            color="primary"
          ></v-text-field>-->
                      <v-text-field
                        v-model="Nacimiento"
                        label="Fecha de nacimiento  con el formato dd/mm/aa "
                        outlined
                        dense
                        color="primary"
                        :rules="[rules.required]"
                      ></v-text-field>
                    </div>
                  </v-form>
                </div>
                <v-card-actions class="d-flex justify-center">
                  <div class="d-flex justify-center">
                    <v-btn
                      height="50"
                      class="btn-center white--text rounded-xl ma-6"
                      depressed
                      color="#34A853"
                      :disabled="!formularioCompleto"
                      @click="crearMascota"
                    >
                      Guardar
                    </v-btn>
                    <v-btn
                      height="50"
                      class="btn-center white--text rounded-xl ma-6"
                      depressed
                      color="#FF5252"
                      @click="dialogCrear = false"
                    >
                      Cancelar
                    </v-btn>
                  </div>
                </v-card-actions>
              </v-card>
            </v-dialog>
            <!-- -->
          </v-row>
          <v-row class="">
            <v-card
              width="213"
              class="rounded-xl mx-4 mt-2"
              height="290"
              elevation="14"
              v-for="mascota in mascotas"
              :key="mascota.id_mascota"
              ><v-list
                ><v-list-item class="d-flex justify-center">
                  <v-list-item-icon>
                    <v-btn
                      icon
                      color="red"
                      @click="openDialogDelete(mascota.id_mascota)"
                    >
                      <v-icon color="red">mdi-trash-can-outline</v-icon>
                    </v-btn>
                  </v-list-item-icon>

                  <v-list-item-content class="d-flex justify-center">
                    <div class="d-flex justify-center">
                      <v-list-item-subtitle class="ml-1">
                        {{ mascota.especie_mascota }}</v-list-item-subtitle
                      >
                    </div>
                  </v-list-item-content>
                  <v-list-item-icon>
                    <v-btn
                      color="#5CBBF6"
                      icon
                      @click="openDialogEdit(mascota.id_mascota)"
                    >
                      <v-icon color="#5CBBF6">mdi-pencil</v-icon>
                    </v-btn>
                  </v-list-item-icon>
                </v-list-item>
                <v-list-item class="d-flex justify-center">
                  <v-avatar color="blue-grey lighten-4">
                    <template v-if="mascota.foto_mascota">
                      <v-img
                        :src="'data:image/png;base64,' + mascota.foto_mascota"
                      ></v-img>
                    </template>
                    <template v-else>
                      <v-icon>mdi-paw</v-icon>
                    </template>
                  </v-avatar></v-list-item
                >
                <v-list-item>
                  <v-list-item-subtitle class="d-flex justify-center">
                    <v-btn text small rounded @click="XD(mascota.id_mascota)">
                      {{ mascota.nombre_mascota }}
                    </v-btn></v-list-item-subtitle
                  >
                </v-list-item>

                <v-list-item>
                  <v-list-item-subtitle class="d-flex justify-center"
                    >{{ mascota.raza_mascota }} -

                    {{
                      moment(mascota.fecha_nacimiento_mascota)
                        .locale("es")
                        .format("DD/MM/YY")
                    }}
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="d-flex justify-center"
                  ><v-btn
                    rounded
                    dark
                    color="#5CBBF6"
                    @click="GG(mascota.id_mascota)"
                  >
                    Agendar cita
                    <v-icon right>mdi-plus</v-icon>
                  </v-btn>
                </v-list-item>
              </v-list></v-card
            >
            <v-row v-if="mascotas.length === 0" class="d-flex justify-center">
              <h2 class="py-7">No hay mascotas</h2>
            </v-row>
          </v-row>
        </v-col>
      </v-row>
      <v-dialog v-model="dialogEliminar" width="500">
        <v-card class="rounded-xl">
          <div class="d-flex justify-center pt-7">
            <v-icon large color="yellow" dark> mdi-alert </v-icon>
          </div>
          <div class="d-flex justify-center pt-7">
            <h3>Dar de baja mascota</h3>
          </div>
          <div class="d-flex justify-center pt-7">
            ¿Está seguro que desea dar de baja la mascota del usuario?
          </div>
          <v-card-actions class="d-flex justify-center">
            <div class="d-flex justify-center">
              <v-btn
                height="50"
                class="btn-center white--text rounded-xl ma-6"
                depressed
                color="#34A853"
                @click="eliminarMascota()"
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
      <v-dialog v-model="dialogEditar" width="500">
        <v-card class="rounded-xl">
          <v-container class="px-10">
            <v-form>
              <div class="text-center my-1 py-1">
                <v-text-field
                  v-model="nombre"
                  label="Nombre"
                  outlined
                  dense
                  color="primary"
                ></v-text-field>

                <v-text-field
                  v-model="color"
                  label="Color"
                  outlined
                  dense
                  color="primary"
                ></v-text-field>

                <v-text-field
                  v-model="raza"
                  label="Raza"
                  outlined
                  dense
                  color="primary"
                ></v-text-field>
                <v-text-field
                  v-model="padecimientos"
                  label="Padecimientos"
                  outlined
                  dense
                  color="primary"
                ></v-text-field>
              </div>
            </v-form>
          </v-container>

          <v-card-actions class="d-flex justify-center">
            <div class="d-flex justify-center">
              <v-btn
                height="50"
                class="btn-center white--text rounded-xl ma-6"
                depressed
                color="#34A853"
                @click="editarMascota(nombre, color, raza, padecimientos)"
              >
                ACEPTAR
              </v-btn>
              <v-btn
                height="50"
                class="btn-center white--text rounded-xl ma-6"
                depressed
                color="#FF5252"
                @click="dialogEditar = false"
              >
                Cancelar
              </v-btn>
            </div>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-container>
  </v-app>
</template>

<script lang="ts">
import axios from "axios";
import moment from "moment";
import { component } from "vue/types/umd";

export default {
  data() {
    return {
      items: ["Macho", "Hembra"],
      usuario: [],
      mascotas: [],
      citas: [],
      moment: moment,
      dialogEliminar: false,
      idMascota: 0,
      dialogEditar: false,
      dialogCrear: false,
      nombre: "",
      color: "",
      raza: "",
      padecimientos: "",
      NombreM: "",
      Color: "",
      Especie: "",
      Raza: "",
      Nacimiento: "",
      sexo: "",
      rules: {
        required: (value: any) => !!value || "Campo Requerido",
      },
    };
  },
  computed: {
    formularioCompleto() {
      return (
        this.NombreM &&
        this.sexo &&
        this.Color &&
        this.Especie &&
        this.Raza &&
        this.Nacimiento
      );
    },
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
    XD(id: string) {
      console.log("XDDDD", id);
      this.$router.push("/XD/" + id + "/perfilMascota");
    },
    GG(id: string) {
      console.log("XDDDD", id);
      this.$router.push("/XD/" + id + "/newCita");
    },
    formatDate(Nacimiento: moment.MomentInput) {
      return moment(Nacimiento, "DD-MM-YYYY").format("YYYY-MM-DD");
    },
    onSexoSelect() {
      this.sexo = this.sexo.trim();
      console.log("no se ", this.sexo);
      console.log(parseInt(this.$route.params.Clientes));
      // Agrega esto si quieres eliminar espacios en blanco al inicio y al final del valor seleccionado
    },
    eliminarMascota() {
      axios
        .get("http://localhost:8080/xampp/axios/api/EliminarMascota.php", {
          params: {
            id_mascota: this.idMascota,
          },
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log(response.data);
          this.dialogEliminar = false;
          //window.location.reload();
          // Actualizar la lista de mascotas para reflejar el cambio
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },
    editarMascota(
      nombre_mascota: string,
      color_mascota: string,
      raza_mascota: string,
      padecimientos_mascota: string
    ) {
      axios
        .get("http://localhost:8080/xampp/axios/api/editarMascota.php", {
          params: {
            id_mascota: this.idMascota,

            nombre_mascota: this.nombre,
            color_mascota: this.color,
            raza_mascota: this.raza,
            padecimientos_mascota: this.padecimientos,
          },
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log(response.data);

          this.dialogEditar = false;
          // window.location.reload();
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },
    crearMascota() {
      console.log(
        this.$route.params.Clientes,
        this.formatDate(this.Nacimiento),
        this.sexo
      );
      axios
        .get("http://localhost:8080/xampp/axios/api/crearMascota.php", {
          params: {
            id_usuario: this.$route.params.Clientes,
            nombre_mascota: this.NombreM,
            color_mascota: this.Color,
            raza_mascota: this.Raza,
            especie_mascota: this.Especie,
            fecha_nacimiento_mascota: this.formatDate(this.Nacimiento),
            sexo_mascota: this.sexo,
          },
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log(response.data);
          this.dialogCrear = false;
          // window.location.reload();
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },
    actualizar() {
      // traer usuario
      axios
        .get("http://localhost:8080/xampp/axios/api/traerUser.php", {
          params: {
            id_usuario: parseInt(this.$route.params.Clientes), //ahorita
          },
        })
        .then((response) => {
          this.usuario = response.data;
          console.log(this.$route.params.Clientes);
          console.log(this.usuario);
        })
        .catch((error) => {
          console.error(error);
        });
      //nueva traer mascotas
      axios
        .get("http://localhost:8080/xampp/axios/api/trareMascotas.php", {
          params: {
            id_usuario: parseInt(this.$route.params.Clientes),
          },
        })
        .then((response) => {
          this.mascotas = response.data;
          console.log(this.$route.params.Clientes);
          console.log(this.mascotas);
        })
        .catch((error) => {
          console.error(error);
        });
      /// traer resumen de citas
      axios
        .get("http://localhost:8080/xampp/axios/api/CitasUsuario.php", {
          params: {
            id_usuario: parseInt(this.$route.params.Clientes),
          },
        })
        .then((response) => {
          this.citas = response.data;
          console.log(this.$route.params.Clientes);
          console.log(this.citas);
        })
        .catch((error) => {
          console.error(error);
        });
    },

    openDialogDelete(id_mascota: number) {
      this.dialogEliminar = true;
      this.idMascota = id_mascota;
    },
    openDialogEdit(id_mascota: number) {
      this.dialogEditar = true;
      this.idMascota = id_mascota;
    },
  },

  mounted() {
    this.actualizar(); // Ejecuta la función una vez cuando se carga el componente
    setInterval(this.actualizar, 2000);
    const existe = this.checkCookie();
    if (existe) {
      console.log("La cookie existe");
    } else {
      this.$router.push("/");
    }
  },
};
</script>

<style></style>
