<template>
  <div>
    <nav-l></nav-l>
    <!-------- naveacion derecha-->
    <nav-r></nav-r>
    <!--central-->
    <!--central-->

    <v-container>
      <h2 class="py-7">Citas pendientes</h2>
      <v-row>
        <v-col cols="12" sm="3" md="3">
          <v-card class="rounded-xl" elevation="14" outlined min-height="204.8"
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
                      <div class="text-start"></div
                    ></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-content>
            </v-list-item>
          </v-card>
        </v-col>
        <v-col cols="12" sm="6" md="7">
          <v-card class="rounded-xl" elevation="14" outlined min-height="204.8"
            ><v-list-item three-line>
              <v-list-item-content>
                <v-list-item-title class="text-h5 mb-1">
                  Detalles
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
          <v-card class="rounded-xl" elevation="14" outlined min-height="204.8">
            <v-card-title class="justify-center text-h5">Hora</v-card-title>

            <v-card-text class="justify-cente mt-4">
              <div class="text-center">
                <v-btn icon depressed>
                  <v-icon x-large>mdi-clock-time-four-outline</v-icon>
                  <div>
                    <p class="text-h5">
                      {{ moment(cita.hora_cita, "HH:mm:ss").format("h:mm a") }}
                    </p>
                  </div>
                </v-btn>
              </div>
            </v-card-text>
            <v-card-text> </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="12" md="12">
          <v-card elevation="14" outlined class="rounded-xl">
            <v-col sm="12" md="12" lg="12">
              <v-card-title
                ><h2 class="py-7">Citas pendientes</h2></v-card-title
              >
              <v-card-text>
                <v-form ref="form">
                  <div class="text-center my-1 py-1">
                    <v-select
                      rounded
                      v-model="tipo"
                      :items="items"
                      label="Motivo"
                      @input="onTipoSelect"
                      outlined
                      chips
                      :rules="[rules.required]"
                    ></v-select>
                  </div>

                  <v-row>
                    <v-col cols="6" sm="6" md="6">
                      <v-text-field
                        rounded
                        dense
                        label="Proxima aplicacion"
                        outlined
                        v-model="ProximaA"
                      ></v-text-field>
                    </v-col>
                    <v-col cols="6" sm="6" md="6">
                      <v-text-field
                        rounded
                        dense
                        label="Peso de mascota"
                        outlined
                        v-model="PesoM"
                        :rules="[rules.required]"
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-text-field
                        rounded
                        dense
                        label="Producto"
                        outlined
                        v-model="Producto"
                        :rules="[rules.required]"
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-text-field
                        rounded
                        dense
                        label="Quien aplico"
                        outlined
                        v-model="Aplico"
                        :rules="[rules.required]"
                      ></v-text-field>
                    </v-col>
                  </v-row>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      rounded
                      v-model="Des"
                      label="Descripcion"
                      outlined
                      dense
                      color="primary"
                      :rules="[rules.required]"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      rounded
                      v-model="Observa"
                      label="Observaciones"
                      outlined
                      dense
                      color="primary"
                    ></v-text-field>
                  </div>
                </v-form>
                <v-card-actions class="d-flex justify-center">
                  <div class="text-center">
                    <v-btn
                      height="40"
                      class="btn-center mx-5"
                      dark
                      rounded
                      color="success"
                      depressed
                      :disabled="!formularioCompleto"
                      @click="crearConsulta(cita.id_mascota)"
                    >
                      Terminar cita
                    </v-btn>

                    <v-btn
                      height="40"
                      class="btn-center"
                      dark
                      rounded
                      color="#5C0FD9"
                      :disabled="!formularioCompleto"
                      @click="Terminarconsulta(cita.id_mascota)"
                    >
                      Agendar nueva cita
                    </v-btn>
                  </div>
                </v-card-actions>
              </v-card-text>
            </v-col>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
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
      items: ["Vacunacion", "Medica", "Estetica"],
      tipo: "",
      FechaA: "",
      ProximaA: "",
      PesoM: "",
      Producto: "",
      Aplico: "",
      Des: "",
      Observa: "",
      idmascota: "",
      cita: [],
      moment: moment,
      rules: {
        required: (value: any) => !!value || "Campo Requerido",
      },
    };
  },
  mounted() {
    // traer datos de consulta
    axios
      .get("http://localhost:8080/xampp/axios/api/traerCitaparacons.php", {
        params: {
          id_cita: parseInt(this.$route.params.Citas), //ahorita
        },
      })
      .then((response) => {
        this.cita = response.data;
        console.log(response.data);
      })
      .catch((error) => {
        console.error(error);
      });
    const existe = this.checkCookie();
    if (existe) {
      console.log("La cookie existe");
    } else {
      this.$router.push("/");
    }
  },
  computed: {
    formularioCompleto() {
      return (
        this.tipo && this.PesoM && this.Producto && this.Aplico && this.Des
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
    formatDate(ProximaA: moment.MomentInput) {
      return moment(ProximaA, "DD-MM-YYYY").format("YYYY-MM-DD");
    },
    onTipoSelect() {
      this.tipo = this.tipo.trim();

      // Agrega esto si quieres eliminar espacios en blanco al inicio y al final del valor seleccionado
    },
    crearConsulta(idmascota: string) {
      console.log(parseInt(idmascota));

      axios
        .post("http://localhost:8080/xampp/axios/api/CrearConsulta.php", {
          id_usuario: parseInt(this.$route.params.Clientes),
          tipo_consulta: this.tipo,
          proxima_cita_consulta: this.formatDate(this.ProximaA),
          peso_consulta: this.PesoM,
          producto_consulta: this.Producto,
          aplico_consulta: this.Aplico,
          descripcion_consulta: this.Des,
          observaciones_consulta: this.Observa,
          id_mascota: parseInt(idmascota),
          id_cita: parseInt(this.$route.params.Citas),
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          //window.location.reload();
          window.history.back();
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },
    Terminarconsulta(idmascota: string) {
      console.log(parseInt(idmascota));

      axios
        .post("http://localhost:8080/xampp/axios/api/CrearConsulta.php", {
          id_usuario: parseInt(this.$route.params.Clientes),
          tipo_consulta: this.tipo,
          proxima_cita_consulta: this.formatDate(this.ProximaA),
          peso_consulta: this.PesoM,
          producto_consulta: this.Producto,
          aplico_consulta: this.Aplico,
          descripcion_consulta: this.Des,
          observaciones_consulta: this.Observa,
          id_mascota: parseInt(idmascota),
          id_cita: parseInt(this.$route.params.Citas),
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          //window.location.reload();

          this.$router.push("/XD/" + idmascota + "/newCita");
        })
        .catch((error) => {
          // Manejar el error
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
