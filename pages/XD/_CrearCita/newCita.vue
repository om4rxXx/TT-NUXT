<template>
  <v-app>
    <nav-l></nav-l>

    <v-container>
      <h2 class="py-7"></h2>

      <v-card flat rounded="xl" elevation="14" outlined
        ><div><p></p></div>
        <div class="d-flex justify-center">
          <v-card-title>Agendar Cita</v-card-title>
        </div>
        <v-form>
          <v-container>
            <v-row>
              <v-col sm="6" md="6"
                ><div class="text-center pl-12">
                  <v-card flat>
                    <v-row class="pb-5">
                      <v-col sm="3" md="3">
                        <v-avatar size="90" color="blue-grey lighten-4">
                          <template v-if="mascota.foto_mascota">
                            <v-img
                              :src="
                                'data:image/png;base64,' + mascota.foto_mascota
                              "
                            ></v-img>
                          </template>
                          <template v-else>
                            <v-icon>mdi-paw</v-icon>
                          </template>
                        </v-avatar></v-col
                      >
                      <v-col sm="4" md="4">
                        <v-list dense nav>
                          <v-list-item>
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
                              <v-list-item-title
                                >Especie:
                                {{ mascota.especie_mascota }}</v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                        </v-list></v-col
                      >
                      <v-col sm="5" md="5">
                        <v-list dense nav>
                          <v-list-item>
                            <v-list-item-content>
                              <v-list-item-title
                                >Nacimiento:{{
                                  " " +
                                  moment(mascota.fecha_nacimiento_mascota)
                                    .locale("es")
                                    .format("DD/MM/YY")
                                }}</v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                          <v-list-item>
                            <v-list-item-content>
                              <v-list-item-title
                                >Dueño: {{ mascota.nombre_usuario }}
                                {{
                                  mascota.apellido_usuario
                                }}</v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                        </v-list></v-col
                      >
                    </v-row>
                  </v-card>

                  <v-select
                    v-model="tipo"
                    :items="items"
                    label="Tipo de cita"
                    @input="onTipoSelect"
                    outlined
                    chips
                    :rules="[rules.required]"
                  ></v-select>
                  <v-text-field
                    dense
                    label="Descripcion"
                    outlined
                    v-model="Descri"
                    :rules="[rules.required]"
                  ></v-text-field>
                  <v-text-field
                    dense
                    label="Observaciones"
                    outlined
                    v-model="Observaciones"
                  ></v-text-field>
                  <v-select
                    :items="ocupados12"
                    label="Horario"
                    outlined
                    chips
                    v-model="Hora"
                    :rules="[rules.required]"
                  ></v-select></div
              ></v-col>
              <v-col sm="6" md="6">
                <div class="d-flex justify-center">
                  <v-date-picker
                    class="rounded-xl"
                    dark
                    locale="spanish"
                    v-model="date"
                    elevation="15"
                    :min="minDate"
                    :allowed-dates="allowedDates"
                    @input="sendDateToServer"
                  ></v-date-picker>
                </div>
              </v-col>
            </v-row>
          </v-container>
          <div class="d-flex justify-center">
            <v-btn
              height="50"
              class="btn-center white--text rounded-xl ma-6"
              depressed
              color="#5C0FD9"
              @click="crearCita(mascota.id_usuario)"
            >
              Agendar
            </v-btn>
            <v-btn
              height="50"
              class="btn-center white--text rounded-xl ma-6"
              depressed
              color="#FF5252"
              @click="XD"
            >
              Cancelar
            </v-btn>
          </div>
        </v-form>
      </v-card>
    </v-container>
  </v-app>
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
      Tipo: "",
      Hora: "",
      Descri: "",
      Observaciones: "",
      date: "",
      idusuario: "",
      items: ["Vacunacion", "Medica", "Estetica"],
      hora: [
        "10:00 AM",
        "10:30 AM",
        "11:00 AM",
        "11:30 AM",
        "12:00 PM",
        "12:30 PM",
        "1:00 PM",
        "1:30 PM",
        "2:00 PM",
        "2:30 PM",
        "3:00 PM",
        "3:30 PM",
        "4:00 PM",
        "4:30 PM",
        "5:00 PM",
        "5:30 PM",
        "6:00 PM",
      ],
      ocupados24: [],
      ocupados12: [] as String[],
      tipo: "",
      moment: moment,
      picker: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
        .toISOString()
        .substr(0, 10),

      minDate: new Date(Date.now() - 8640000).toISOString().substr(0, 10),
      mascota: [],
      rules: {
        required: (value: any) => !!value || "Campo Requerido",
      },
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
    //console.log(this.$route.params.mascota);
    axios
      .get("http://localhost:8080/xampp/axios/api/traerMascota.php", {
        params: {
          id_mascota: parseInt(this.$route.params.CrearCita), //ahorita
        },
      })
      .then((response) => {
        this.mascota = response.data;
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
    XD() {
      this.$router.push("/XD/Principal");
    },
    formatDate(ocupados24: moment.MomentInput[], horas: string[]) {
      const ocupados12 = ocupados24.map((hora) =>
        moment(hora, "HH:mm").format("h:mm A")
      );

      return horas.filter((hora) => !ocupados12.includes(hora));
    },
    sendDateToServer() {
      axios
        .get("http://localhost:8080/xampp/axios/api/HorasDisponibles.php", {
          params: {
            fecha_cita: this.date, // suponiendo que tienes una variable 'numero' en tu componente Vue
          },
        })
        .then((response) => {
          this.ocupados24 = response.data;
          this.ocupados12 = this.formatDate(this.ocupados24, this.hora);
          //console.log(this.ocupados24);
          // console.log("XD", this.formatDate(this.ocupados24, this.hora));
        })
        .catch((error) => {
          this.ocupados12 = this.hora;
          console.error("Error updating date on server:", error);
        });
    },
    allowedDates(date: string | number | Date) {
      // Obtenemos el día de la semana (0 = domingo, 6 = sábado)
      const dayOfWeek = new Date(date).getDay();

      // Permitimos solo las fechas que no son sábado ni domingo
      return dayOfWeek !== 6 && dayOfWeek !== 6;
    },
    onTipoSelect() {
      this.tipo = this.tipo.trim();
      // console.log("hola pend", this.tipo.trim());
      // Agrega esto si quieres eliminar espacios en blanco al inicio y al final del valor seleccionado
    },
    crearCita(idusuario: string) {
      //console.log(moment(this.hora, "h:mm A").format("HH:mm "));

      axios
        .get("http://localhost:8080/xampp/axios/api/CrearCita.php", {
          params: {
            id_mascota: this.$route.params.CrearCita,
            tipo_cita: this.tipo.trim(),
            descripcion_cita: this.Descri, //this.formatDate(this.ProximaA),
            observaciones_cita: this.Observaciones,
            fecha_cita: this.date,
            hora_cita: moment(this.hora, "h:mm A").format("HH:mm "),
            id_usuario: idusuario,
          },
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          //window.location.reload();
          //console.error("XD");
          this.$router.push("/XD/Principal");
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },
  },
};
</script>

<style></style>
