<template>
  <v-app>
    <v-app-bar class="py-2" app dense flat max-height="50" color="white"
      ><v-avatar class="pa-10">
        <img src="~/assets/images/logito.png" alt="John" />
      </v-avatar>

      <v-toolbar-title>Mr Can</v-toolbar-title>
    </v-app-bar>

    <div><p></p></div>
    <v-row class="d-flex justify-center">
      <v-col cols="6">
        <v-card
          elevation="14"
          rounded="200"
          class="mx-auto my-16 rounded-lg width-auto"
          color="white"
        >
          <v-card-text>
            <div>
              <p class="text-h4 text-color d-flex justify-center">
                <v-avatar class="pa-10" size="160">
                  <img src="~/assets/images/logito.png" alt="John" />
                </v-avatar>
              </p>
              <p class="text-h4 text-color d-flex justify-center">Mr can</p>
              <p class="text-h7 text-color d-flex justify-center">
                Iniciar Sesión {{ post.id }}
              </p>
            </div>
            <div class="d-flex justify-center">
              <v-form ref="form" v-model="valid" lazy-validation>
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
                    max-width="20"
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
              </v-form>
            </div>

            <div class="d-flex justify-end mr-12 pr-12">
              <a
                href="https://www.leagueoflegends.com/es-mx/"
                class="text-decoration-none mr-10 pr-10"
                >¿Olvidaste la contraseña?</a
              >
            </div>
            <p></p>
            <div class="d-flex justify-center">
              <v-btn
                min-width="300"
                min-height="50"
                class="btn-center white--text"
                depressed
                color="#3D76F2"
                :loading="loading"
                @click="createUser"
                to="/Main/Main"
              >
                Iniciar Sesión
              </v-btn>
            </div>
            <p></p>
            <div class="d-flex justify-center">
              <v-btn text to="/Reister">Registrar</v-btn>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-footer app color="primary lighten-1" padless>
      <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
        <strong>Mr Can</strong>
      </v-col>
      <v-col class="primary py-4 text-center white--text" cols="12">
        {{ new Date().getFullYear() }} — Vuetify
      </v-col>
    </v-footer>
  </v-app>
</template>
<script>
export default {
  data() {
    return {
      show1: false,
      valid: false,
      show2: true,
      email: "",
      loading: false,
      post: {
        type: Object,
        default: {},
      },

      password: "Password",
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },
    };
  },
  created: function () {
    fetch("https://jsonplaceholder.typicode.com/posts/1")
      .then((response) => {
        return response.json();
      })
      .then((result) => {
        this.post = result;
      });
  },
};
</script>

<style>
.text-color {
  color: #3d76f2;
}
.v-text-field {
  width: 400px;
}
</style>
