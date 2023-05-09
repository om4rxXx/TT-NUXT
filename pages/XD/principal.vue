<template>
  <div>
    <v-app>
      <nav-l></nav-l>
      <!-------- naveacion derecha-->
      <nav-r></nav-r>
      <!--central-->
      <main>
        <v-container>
          <h2 class="py-7">Citas pendientes</h2>

          <v-row v-for="cita in citas" :key="cita.id_cita">
            <v-col cols="12" sm="3" md="3">
              <v-card
                class="rounded-xl"
                elevation="14"
                outlined
                min-height="204.8"
                ><v-list-item three-line>
                  <v-list-item-content>
                    <v-list-item-title class="text-h5 mb-1">
                      {{ cita.tipo_cita }}
                    </v-list-item-title>

                    <v-list-item class="md-4">
                      <v-list-item-content>
                        <v-list-item-title>Nombre:</v-list-item-title>
                      </v-list-item-content>
                      <v-list-item-content>
                        <v-list-item-title
                          ><h4>
                            {{ cita.nombre_mascota }}
                          </h4></v-list-item-title
                        >
                      </v-list-item-content>
                    </v-list-item>
                    <v-list-item class="md-4">
                      <v-list-item-content>
                        <v-list-item-title>Raza:</v-list-item-title>
                      </v-list-item-content>
                      <v-list-item-content>
                        <v-list-item-title
                          ><h4>{{ cita.raza_mascota }}</h4></v-list-item-title
                        >
                      </v-list-item-content>
                    </v-list-item>
                    <v-list-item class="md-4">
                      <v-list-item-content>
                        <v-list-item-title>
                          <div class="text-start">
                            <a
                              class="text-decoration-none mr-10 pr-10"
                              @click="openDialog(cita.id_mascota)"
                              >Detalles</a
                            >
                          </div></v-list-item-title
                        >
                      </v-list-item-content>
                    </v-list-item>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-col>
            <v-col cols="12" sm="5" md="6">
              <v-card
                class="rounded-xl"
                elevation="14"
                outlined
                min-height="204.8"
                ><v-list-item three-line>
                  <v-list-item-content>
                    <v-list-item-title class="text-h5 mb-1">
                      Detalles de cita
                    </v-list-item-title>
                    <v-list-item class="md-4">
                      <v-list-item-content>
                        <v-list-item-title>{{
                          cita.descripcion_cita
                        }}</v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-col>
            <v-col cols="12" sm="5" md="3">
              <v-card
                class="rounded-xl"
                elevation="14"
                outlined
                min-height="204.8"
              >
                <v-card-title class="justify-center text-h5">Hora</v-card-title>

                <v-card-text class="justify-cente mt-4">
                  <div class="text-center">
                    <v-btn icon disabled>
                      <v-icon x-large>mdi-clock-time-four-outline</v-icon>
                      <div>
                        <p class="text-h5">
                          {{
                            moment(cita.fecha_cita)
                              .locale("es")
                              .format("DD/MM/YY")
                          }}
                          {{
                            moment(cita.hora_cita, "HH:mm:ss").format("h:mm a")
                          }}
                        </p>
                      </div>
                    </v-btn>
                  </div>
                </v-card-text>
                <v-card-text>
                  <v-row class="d-flex justify-center justify-space-around">
                    <v-hover v-slot="{ hover }" open-delay="50">
                      <v-btn
                        depressed
                        :elevation="hover ? 16 : 2"
                        :class="{ 'on-hover': hover }"
                        color="#5CBBF6"
                        rounded
                        dark
                        @click="XD(cita.id_cita)"
                      >
                        Iniciar
                      </v-btn>
                    </v-hover>
                    <v-hover v-slot="{ hover }" open-delay="50">
                      <v-btn
                        :elevation="hover ? 16 : 2"
                        :class="{ 'on-hover': hover }"
                        depressed
                        color="#FF5252"
                        rounded
                        dark
                        @click="openDialogDelete(cita.id_cita)"
                      >
                        Eliminar
                      </v-btn>
                    </v-hover>
                  </v-row>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
          <v-row v-if="citas.length === 0" class="d-flex justify-center">
            <h2 class="py-7">No hay citas pendientes</h2>
          </v-row>
          <v-dialog v-model="dialogEliminar" width="500">
            <v-card class="rounded-xl">
              <div class="d-flex justify-center pt-7">
                <v-icon large color="yellow" dark> mdi-alert </v-icon>
              </div>
              <div class="d-flex justify-center pt-7">
                <h3>Eliminar cita</h3>
              </div>
              <div class="d-flex justify-center pt-7">
                Esta seguro que desea eliminar esta cita?
              </div>
              <v-card-actions class="d-flex justify-center">
                <div class="d-flex justify-center">
                  <v-btn
                    height="50"
                    class="btn-center white--text rounded-xl ma-6"
                    depressed
                    color="#34A853"
                    @click="eliminarCita()"
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
          <v-dialog v-model="dialog" width="500" class="rounded-xl">
            <v-card class="rounded-xl">
              <v-card-title class="d-flex justify-center">
                {{ mascota.nombre_mascota }}
              </v-card-title>

              <p class="text-h4 text-color d-flex justify-center">
                <v-avatar color="blue-grey lighten-4" size="100">
                  <template v-if="mascota.foto_mascota">
                    <v-img
                      :src="'data:image/png;base64,' + mascota.foto_mascota"
                    ></v-img>
                  </template>
                  <template v-else>
                    <v-icon>mdi-paw</v-icon>
                  </template>
                </v-avatar>
              </p>

              <v-card-text>
                <v-list>
                  <v-list-item-title class="d-flex justify-center"
                    >Dueño: {{ mascota.nombre_usuario }}
                    {{ mascota.apellido_usuario }}
                  </v-list-item-title>
                  <v-list-item-title class="d-flex justify-center"
                    >Especie: {{ mascota.especie_mascota }}
                  </v-list-item-title>
                  <v-list-item-title class="d-flex justify-center text-h6"
                    >Datos</v-list-item-title
                  >
                  <v-row>
                    <v-col sm="6" class="text-h5">
                      <p>Sexo:</p>
                      <p>Raza:</p>
                      <p>Nacimiento:</p></v-col
                    >
                    <v-col sm="6" class="text-h5">
                      <p class="d-flex justify-end">
                        {{ mascota.sexo_mascota }}
                      </p>
                      <p class="d-flex justify-end">
                        {{ mascota.raza_mascota }}
                      </p>
                      <p class="d-flex justify-end">
                        {{
                          moment(mascota.fecha_nacimiento_mascota)
                            .locale("es")
                            .format("DD/MM/YY")
                        }}
                      </p></v-col
                    >
                  </v-row>
                </v-list>
              </v-card-text>
              <div class="d-flex justify-center">
                <v-btn
                  color="#FF5252"
                  @click="dialog = false"
                  class="rounded-xl ma-6 white--text"
                >
                  Cerrar
                </v-btn>
              </div>
            </v-card>
          </v-dialog>
        </v-container>
      </main>
    </v-app>
  </div>
</template>

<script lang="ts">
import axios from "axios";
import moment from "moment";
import NavL from "~/components/NavL.vue";
import NavR from "~/components/NavR.vue";
export default {
  components: {
    NavL,
    NavR,
  },

  data() {
    return {
      dialog: false,
      moment: moment,
      idMascota: 0,
      dialogEliminar: false,
      citas: [],
      mascota: [],
      idCita: 0,
    };
  },

  mounted() {
    this.actualizarCitas(); // Ejecuta la función una vez cuando se carga el componente
    setInterval(this.actualizarCitas, 5000);
    // Ejecuta la función cada 5 segundos

    const existe = this.checkCookie();
    if (existe) {
      console.log("La cookie existe");
    } else {
      this.$router.push("/");
    }
  },
  methods: {
    eliminarCita() {
      axios
        .get("http://localhost:8080/xampp/axios/api/EliminarCita.php", {
          params: {
            id_cita: this.idCita,
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
    openDialogDelete(id_cita: number) {
      this.dialogEliminar = true;
      this.idCita = id_cita;
    },
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
      this.$router.push(id + "/Consulta");
    },
    actualizarCitas() {
      axios
        .get("http://localhost:8080/xampp/axios/api/ListarCitasConmascotas.php")
        .then((response) => {
          // Actualiza los datos en el estado de tu componente
          this.citas = response.data;
          console.log(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    },

    openDialog(id_mascota: number) {
      this.dialog = true;
      this.idMascota = id_mascota;
      axios
        .get("http://localhost:8080/xampp/axios/api/traerMascota.php", {
          params: {
            id_mascota: this.idMascota, //ahorita
          },
        })
        .then((response) => {
          this.mascota = response.data;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

<style>
.v-btn__content {
  display: flex;
  flex-direction: column;
}
</style>
