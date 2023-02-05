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
                          <div class="text-start">
                            <v-dialog
                              v-model="dialog"
                              width="500"
                              class="rounded-xl"
                            >
                              <template v-slot:activator="{ on, attrs }">
                                <a
                                  v-bind="attrs"
                                  v-on="on"
                                  class="text-decoration-none mr-10 pr-10"
                                  >Detalles</a
                                >
                              </template>

                              <v-card class="rounded-xl">
                                <v-card-title class="d-flex justify-center">
                                  Pochita
                                </v-card-title>
                                <p class="d-flex justify-center">
                                  Nacimiento: 12/06/2022
                                </p>
                                <p
                                  class="text-h4 text-color d-flex justify-center"
                                >
                                  <v-avatar class="pa-10" size="100">
                                    <img
                                      src="https://cdn.vuetifyjs.com/images/john.jpg"
                                      alt="John"
                                    />
                                  </v-avatar>
                                </p>

                                <v-card-text>
                                  <v-list>
                                    <v-list-item-title
                                      class="d-flex justify-center"
                                      >Dueño: Jesus palafox</v-list-item-title
                                    >
                                    <v-list-item-title
                                      class="d-flex justify-center"
                                      >Especie: Canino</v-list-item-title
                                    >
                                    <v-list-item-title
                                      class="d-flex justify-center text-h6"
                                      >Datos</v-list-item-title
                                    >
                                    <v-row>
                                      <v-col sm="6" class="text-h5"
                                        ><p>Edad:</p>
                                        <p>Sexo:</p>
                                        <p>Raza:</p>
                                        <p>Edad:</p></v-col
                                      >
                                      <v-col sm="6" class="text-h5"
                                        ><p class="d-flex justify-end">15</p>
                                        <p class="d-flex justify-end">
                                          Masculino
                                        </p>
                                        <p class="d-flex justify-end">
                                          Pitbull
                                        </p>
                                        <p class="d-flex justify-end">
                                          ninguno
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
                          </div></v-list-item-title
                        >
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
                <v-card-text>
                  <div class="text-center">
                    <v-btn
                      to="/Main/Consulta"
                      depressed
                      color="#3D76F2"
                      class="white--text"
                    >
                      Iniciar
                    </v-btn>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </main>
    </v-app>
  </div>
</template>

<script ="ts">
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
    };
  },
};
</script>

<style>
.v-btn__content {
  display: flex;
  flex-direction: column;
}
</style>
