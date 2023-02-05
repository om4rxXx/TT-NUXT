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
          <v-card flat rounded="xl" outlined min-height="204.8"
            ><v-list-item three-line>
              <v-list-item-content>
                <v-list-item-title class="text-h5 mb-1">
                  Medica
                </v-list-item-title>
                <v-list-item class="md-4">
                  <v-list-item-content>
                    <v-list-item-title>Nombre:</v-list-item-title>
                  </v-list-item-content>
                  <v-list-item-content>
                    <v-list-item-title><h4>PEPE</h4></v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item class="md-4">
                  <v-list-item-content>
                    <v-list-item-title>Raza:</v-list-item-title>
                  </v-list-item-content>
                  <v-list-item-content>
                    <v-list-item-title><h4>PEPE</h4></v-list-item-title>
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
          <v-card flat rounded="xl" outlined min-height="204.8"
            ><v-list-item three-line>
              <v-list-item-content>
                <v-list-item-title class="text-h5 mb-1">
                  Detalles
                </v-list-item-title>
                <v-list-item class="md-4">
                  <v-list-item-content>
                    <v-list-item-title>Se esta muriendo</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list-item-content>
            </v-list-item>
          </v-card>
        </v-col>
        <v-col cols="12" sm="4" md="2">
          <v-card flat rounded="xl" outlined min-height="204.8">
            <v-card-title class="justify-center text-h5">Hora</v-card-title>

            <v-card-text class="justify-cente mt-4">
              <div class="text-center">
                <v-btn icon depressed>
                  <v-icon x-large>mdi-clock-time-four-outline</v-icon>
                  <div><p class="text-h5">10:30</p></div>
                </v-btn>
              </div>
            </v-card-text>
            <v-card-text> </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="12" md="12">
          <v-card flat rounded="xl" outlined class="rounded-xl">
            <v-col sm="12" md="12" lg="12">
              <v-card-title
                ><h2 class="py-7">Citas pendientes</h2></v-card-title
              >
              <v-card-text>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <div class="text-center my-1 py-1">
                    <v-select
                      :items="items"
                      label="Motivo"
                      outlined
                      chips
                    ></v-select>
                  </div>

                  <v-row>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field
                        dense
                        label="Fecha de aplicacion"
                        outlined
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field
                        dense
                        label="Proxima aplicacion"
                        outlined
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field
                        dense
                        label="Peso de mascota"
                        outlined
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-text-field
                        dense
                        label="Descripcion"
                        outlined
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-text-field
                        dense
                        label="Quien aplico"
                        outlined
                      ></v-text-field>
                    </v-col>
                  </v-row>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="repitPassword"
                      label="Descripcion"
                      outlined
                      dense
                      color="primary"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="repitPassword"
                      label="Observaciones"
                      outlined
                      dense
                      color="primary"
                    ></v-text-field>
                  </div>
                </v-form>

                <div class="text-center">
                  <v-btn
                    height="40"
                    class="btn-center mx-5"
                    dark
                    rounded
                    color="success"
                  >
                    Terminar cita
                  </v-btn>

                  <v-btn
                    height="40"
                    class="btn-center"
                    dark
                    rounded
                    color="#5C0FD9"
                  >
                    Agendar nueva cita
                  </v-btn>
                </div>
              </v-card-text>
            </v-col>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import NavL from "~/components/NavL.vue";
import NavR from "~/components/NavR.vue";

export default {
  components: {
    NavL,
    NavR,
  },
  data: () => ({
    items: ["Vacunacion", "Medica", "Estetica", "Buzz"],
  }),
};
</script>

<style>
.v-btn__content {
  display: flex;
  flex-direction: column;
}
</style>
