<template>
  <v-app>
    <nav-l></nav-l>
    <v-container class="pt-12">
      <v-card flat>
        <v-toolbar color="#5CBBF6" class="rounded-pill" flat>
          <v-avatar class="px-3">
            <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
          </v-avatar>

          <v-toolbar-title class="ml-3 white--text"
            >Jesus palafox</v-toolbar-title
          >
        </v-toolbar>
      </v-card>
      <v-row>
        <v-col sm="4" md="4" lg="4">
          <v-card class="mx-auto my-5 rounded-xl" max-width="374">
            <v-img
              height="250"
              src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
            ></v-img>

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
                    <v-list-item-title>Jesus Palafox Sanchez</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-phone-classic</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>+52 468191589</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-email-fast-outline</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>Veterinario@gmail.com</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-content>
                    <v-list-item-title
                      ><h2>Información adicional</h2></v-list-item-title
                    >
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-calendar-badge-outline</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>11/05/2023</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-icon>
                    <v-icon>mdi-paw</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>80 </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col sm="8" md="8" lg="8">
          <v-card class="rounded-xl mx-auto my-5">
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
                        <v-list-item-title>9</v-list-item-title>
                      </v-list-item-content> </v-list-item
                    ><v-list-item>
                      <v-list-item-icon>
                        <v-icon color="white">mdi-account-circle</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>12</v-list-item-title>
                      </v-list-item-content> </v-list-item
                    ><v-list-item>
                      <v-list-item-icon>
                        <v-icon color="white">mdi-account-circle</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <v-list-item-title>13</v-list-item-title>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <v-row class="px-4 pb-6" justify="space-between">
            <h2>Mascotas</h2>
            <v-dialog v-model="dialog1" width="500">
              <template v-slot:activator="{ on, attrs }">
                <v-btn dark color="#5CBBF6" v-bind="attrs" v-on="on">
                  <v-icon left> mdi-plus </v-icon>
                  Agregar mascota
                </v-btn>
              </template>

              <v-card class="rounded-xl">
                <v-card-title class="text-h5 lighten-2">
                  Nueva mascota
                </v-card-title>
                <div class="d-flex justify-center">
                  <v-form ref="form" v-model="valid" lazy-validation>
                    <div class="text-center my-1 py-1">
                      <v-text-field
                        v-model="NombreM"
                        label="Nombre"
                        outlined
                        dense
                        color="primary"
                      ></v-text-field>
                      <v-select :items="items" label="Sexo" outlined></v-select>
                      <v-text-field
                        v-model="Color"
                        label="Color"
                        outlined
                        dense
                        color="primary"
                      ></v-text-field>
                      <v-text-field
                        v-model="Especie"
                        label="Especie"
                        outlined
                        dense
                        color="primary"
                      ></v-text-field>
                      <v-text-field
                        v-model="Raza"
                        label="Raza"
                        outlined
                        dense
                        color="primary"
                      ></v-text-field>
                      <v-text-field
                        v-model="Nacimiento"
                        label="Feca de nacimiento"
                        outlined
                        dense
                        color="primary"
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
                      :loading="loading"
                      @click="editarUser"
                    >
                      Guardar
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
            <!-- -->
          </v-row>
          <v-row class="">
            <v-card width="213" class="rounded-xl mx-4 mt-2" height="290"
              ><v-list
                ><v-list-item class="d-flex justify-center">
                  <v-list-item-icon>
                    <v-dialog v-model="dialog" width="500">
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn icon color="red" v-bind="attrs" v-on="on">
                          <v-icon color="red">mdi-trash-can-outline</v-icon>
                        </v-btn>
                      </template>

                      <v-card class="rounded-xl">
                        <div class="d-flex justify-center pt-7">
                          <v-icon large color="yellow" dark> mdi-alert </v-icon>
                        </div>
                        <div class="d-flex justify-center pt-7">
                          <h3>Dar de baja mascota</h3>
                        </div>
                        <div class="d-flex justify-center pt-7">
                          ¿Está seguro que desea dar de baja la mascota del
                          usuario?
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
                  </v-list-item-icon>

                  <v-list-item-content class="d-flex justify-center">
                    <div class="d-flex justify-center">
                      <v-list-item-subtitle>Pochita</v-list-item-subtitle>
                    </div>
                  </v-list-item-content>
                  <v-list-item-icon>
                    <v-dialog v-model="dialog" width="500">
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn color="#5CBBF6" icon v-bind="attrs" v-on="on">
                          <v-icon color="#5CBBF6">mdi-pencil</v-icon>
                        </v-btn>
                      </template>

                      <v-card class="rounded-xl">
                        <div class="d-flex justify-center pt-7">
                          <v-avatar size="90">
                            <img
                              src="https://www.hospitalveterinariglories.com/wp-content/uploads/2022/01/26-01-22-American-Bully-conoce-esta-raza-de-perro-.jpg"
                              alt="John"
                            />
                          </v-avatar>
                        </div>
                        <v-container class="px-10">
                          <v-form ref="form" v-model="valid" lazy-validation>
                            <div class="text-center my-1 py-1">
                              <v-text-field
                                v-model="NombreM"
                                label="Nombre"
                                outlined
                                dense
                                color="primary"
                              ></v-text-field>

                              <v-text-field
                                v-model="Color"
                                label="Color"
                                outlined
                                dense
                                color="primary"
                              ></v-text-field>

                              <v-text-field
                                v-model="Raza"
                                label="Raza"
                                outlined
                                dense
                                color="primary"
                              ></v-text-field>
                              <v-text-field
                                v-model="Padecimientos"
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
                  </v-list-item-icon>
                </v-list-item>
                <v-list-item class="d-flex justify-center">
                  <v-avatar>
                    <v-img
                      src="https://ddragon.leagueoflegends.com/cdn/img/champion/splash/Mordekaiser_0.jpg"
                    ></v-img> </v-avatar
                ></v-list-item>
                <v-list-item>
                  <v-list-item-subtitle class="d-flex justify-center"
                    >Pochita</v-list-item-subtitle
                  >
                </v-list-item>

                <v-list-item>
                  <v-list-item-subtitle class="d-flex justify-center"
                    >American bully - 2 años</v-list-item-subtitle
                  >
                </v-list-item>
                <v-list-item class="d-flex justify-center"
                  ><v-btn dark color="#5CBBF6" to="/Main/newCita">
                    <v-icon left> mdi-plus </v-icon>
                    Agendar cita
                  </v-btn>
                </v-list-item>
              </v-list></v-card
            >
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    items: ["Macho", "Hembra"],
  }),
};
</script>

<style></style>
