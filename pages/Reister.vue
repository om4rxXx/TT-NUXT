<template>
  <v-app>
    <v-card flat>
      <v-toolbar color="#5CBBF6" dark class="mx-3 my-1 rounded-pill" flat>
        <v-avatar class="px-3">
          <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
        </v-avatar>

        <v-toolbar-title class="ml-3">Mr Can</v-toolbar-title>
      </v-toolbar>
    </v-card>
    <main>
      <v-card class="rounded-pill" flat tile>
        <div><p></p></div>
        <v-row>
          <v-col cols="12">
            <v-card
              elevation="4"
              rounded="200"
              class="mx-auto my-16 rounded-lg"
              max-width="900"
              color="white"
            >
              <v-card-text>
                <div>
                  <p class="text-h4 text-color d-flex justify-start">
                    Registro
                  </p>
                </div>
                <div class="d-flex justify-center">
                  <v-form>
                    <v-container>
                      <v-row>
                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="Nombre"
                            label="Nombre"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="apellido"
                            label="Apellido"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="telefono"
                            label="Telefono"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="email"
                            label="E-mail"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="estado"
                            label="Estado"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="municipio"
                            label="municipio"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="colonia"
                            label="Colonia"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>

                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="postal"
                            label="C.P."
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>
                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="calle"
                            label="Calle"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>
                        <v-col cols="12" sm="6">
                          <v-text-field
                            v-model="numero"
                            label="Numero Exter"
                            outlined
                            dense
                            color="primary"
                          ></v-text-field>
                        </v-col>
                      </v-row>
                    </v-container>
                  </v-form>
                </div>

                <div class="d-flex justify-center">
                  <v-btn
                    min-width="300"
                    min-height="50"
                    class="btn-center white--text"
                    depressed
                    color="#3D76F2"
                    :loading="loading"
                    @click="createUser"
                  >
                    Iniciar Sesión
                  </v-btn>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
    </main>
  </v-app>
</template>
<script>
export default {};
</script>

<style>
.text-color {
  color: #3d76f2;
}
.v-text-field {
  width: 400px;
}
</style>
