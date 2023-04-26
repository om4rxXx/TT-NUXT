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
                          ><h4>{{ cita.nombre_mascota }}</h4></v-list-item-title
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
            <v-col cols="12" sm="6" md="7">
              <v-card
                class="rounded-xl"
                elevation="14"
                outlined
                min-height="204.8"
                ><v-list-item three-line>
                  <v-list-item-content>
                    <v-list-item-title class="text-h5 mb-1">
                      Detalles {{ cita.descripcion_cita }}
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
            <v-col cols="12" sm="4" md="2">
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
                            moment(cita.hora_cita, "HH:mm:ss").format("h:mm a")
                          }}
                        </p>
                      </div>
                    </v-btn>
                  </div>
                </v-card-text>
                <v-card-text>
                  <div class="text-center">
                    <v-btn
                      depressed
                      color="#5CBBF6"
                      rounded
                      dark
                      @click="XD(cita.id_cita)"
                    >
                      Iniciar
                    </v-btn>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
          <v-dialog v-model="dialog" width="500" class="rounded-xl">
            <v-card class="rounded-xl">
              <v-card-title class="d-flex justify-center">
                {{ mascota.nombre_mascota }}
              </v-card-title>
              <p class="d-flex justify-center">
                Nacimiento:{{
                  moment(mascota.fecha_nacimiento_mascota)
                    .locale("es")
                    .format("DD/MM/YY")
                }}
              </p>
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
                      <p>Edad:</p></v-col
                    >
                    <v-col sm="6" class="text-h5">
                      <p class="d-flex justify-end">
                        {{ mascota.sexo_mascota }}
                      </p>
                      <p class="d-flex justify-end">
                        {{ mascota.raza_mascota }}
                      </p>
                      <p class="d-flex justify-end">
                        {{ mascota.padecimientos_mascota }}
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
      citas: [],
      mascota: [],
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
