<template>
  <v-app>
    <nav-l></nav-l>

    <v-container>
      <h2 class="py-7">Información personal</h2>

      <v-card flat rounded="xl" outlined height="800"
        ><div><p></p></div>
        <v-form>
          <v-container>
            <v-row>
              <v-col sm="4" md="4">
                <v-text-field
                  v-model="Nombre"
                  label="Nombre"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>

                <v-text-field
                  v-model="telefono"
                  label="Telefono"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>

                <v-text-field
                  v-model="estado"
                  label="Estado"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  v-model="colonia"
                  label="Colonia"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  v-model="calle"
                  label="Calle"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  max-width="20"
                  v-model="password"
                  label="Cotraseñaa"
                  outlined
                  dense
                  :type="show1 ? 'text' : 'password'"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  @click:append="show1 = !show1"
                  color="primary"
                  class="py-4"
                ></v-text-field>
              </v-col>
              <v-col sm="4" md="4">
                <v-text-field
                  v-model="apellido"
                  label="Apellido"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>

                <v-text-field
                  v-model="email"
                  label="E-mail"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  v-model="municipio"
                  label="Ciudad"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  v-model="postal"
                  label="C.P."
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  v-model="numeroE"
                  label="Numero Exterior"
                  outlined
                  dense
                  color="primary"
                  class="py-4"
                ></v-text-field>
                <v-text-field
                  max-width="20"
                  v-model="password"
                  label="Cotraseñaa"
                  outlined
                  dense
                  :type="show1 ? 'text' : 'password'"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  @click:append="show1 = !show1"
                  color="primary"
                  class="py-4"
                ></v-text-field>
              </v-col>
              <v-col sm="4" md="4">
                <div class="d-flex justify-center">
                  <v-card width="300" class="rounded-lg">
                    <v-img
                      src="https://picsum.photos/350/165?random"
                      height="150"
                    ></v-img>

                    <v-list
                      ><v-list-item class="md-4">
                        <v-list-item-content>
                          <v-list-item-title
                            ><h2>Foto de perfil</h2></v-list-item-title
                          >
                        </v-list-item-content>
                        <v-list-item-icon>
                          <v-file-input
                            hide-input
                            :rules="img"
                            accept="image/png, image/jpeg, image/bmp"
                            prepend-icon="mdi-pencil"
                          ></v-file-input>
                        </v-list-item-icon> </v-list-item
                    ></v-list>
                  </v-card>
                </div>
              </v-col>
            </v-row>
          </v-container>
          <div class="d-flex justify-center">
            <v-btn
              height="50"
              class="btn-center white--text rounded-xl ma-6"
              depressed
              color="#5CBBF6"
              :loading="loading"
              @click="editarUser"
              to="/Main/Main"
            >
              Guardar
            </v-btn>
            <v-btn
              height="50"
              class="btn-center white--text rounded-xl ma-6"
              depressed
              color="#FF5252"
              :loading="loading"
              to="/Main/Main"
            >
              Cancelar
            </v-btn>
          </div>
        </v-form>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
import NavL from "~/components/NavL.vue";
import NavR from "~/components/NavR.vue";
export default {
  components: {
    NavL,
    NavR,
  },
  data() {
    return {
      show1: false,
      show2: true,

      password: "Password",
      rules: {
        img: (value) =>
          !value ||
          value.size < 2000000 ||
          "Avatar size should be less than 2 MB!",
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },
    };
  },
};
</script>

<style></style>
