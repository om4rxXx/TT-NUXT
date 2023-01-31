<template>
  <v-app>
    <main>
      <v-card flat height="730px" tile>
        <div><p></p></div>
        <v-row>
          <v-col cols="12">
            <v-card class="mx-auto my-16" max-width="744" color="white">
              <v-card-text>
                <p class="text-h4 text--blue my-1 py-5">Register</p>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="name"
                      label="Nombre"
                      outlined
                      dense
                      color="primary"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="lastname"
                      label="Apellido"
                      outlined
                      dense
                      color="primary"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="email"
                      label="E-mail"
                      outlined
                      dense
                      color="primary"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="password"
                      label="Cotraseña"
                      outlined
                      dense
                      :type="show1 ? 'text' : 'password'"
                      :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                      @click:append="show1 = !show1"
                      color="primary"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      v-model="repitPassword"
                      label="Confirmar contraseña"
                      outlined
                      dense
                      :type="show2 ? 'text' : 'password'"
                      :append-icon="show2 ? 'mdi-eye' : 'mdi-eye-off'"
                      @click:append="show2 = !show2"
                      color="primary"
                    ></v-text-field>
                  </div>
                </v-form>

                <div class="d-flex flex-row-reverse">
                  <v-btn class="btn-center mx-5" depressed color="error">
                    Cancelar
                  </v-btn>

                  <v-btn
                    class="btn-center"
                    depressed
                    color="primary"
                    :loading="loading"
                    @click="createUser"
                  >
                    Registrar
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

<style></style>
