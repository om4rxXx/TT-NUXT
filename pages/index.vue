<template>
  <v-app>
    <v-app-bar class="py-2" app dense flat max-height="50" color="white"
      ><v-avatar class="pa-10">
        <img src="~/assets/images/logito.png" alt="John" />
      </v-avatar>

      <v-toolbar-title>Mr Can</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-row class="d-flex justify-center no-scroll">
        <v-col cols="6">
          <v-card
            elevation="14"
            rounded="200"
            class="mx-auto my-16 rounded-xl width-auto"
            color="white"
            absolute
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
                  Iniciar Sesión
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
                      rounded
                      :rules="[rules.emailValido]"
                    ></v-text-field>
                  </div>
                  <div class="text-center my-1 py-1">
                    <v-text-field
                      max-width="20"
                      v-model="password"
                      label="Cotraseña"
                      outlined
                      dense
                      rounded
                      :type="show1 ? 'text' : 'password'"
                      :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                      @click:append="show1 = !show1"
                      color="primary"
                      :rules="[rules.required]"
                    ></v-text-field>
                  </div>
                </v-form>
              </div>

              <div class="d-flex justify-end">
                <v-btn to="/recuperar" text>
                  <a class="text-decoration-none"
                    >¿Olvidaste la contraseña?
                  </a></v-btn
                >
              </div>
              <p></p>
              <div class="d-flex justify-center">
                <v-btn
                  min-width="300"
                  min-height="50"
                  class="btn-center white--text"
                  depressed
                  rounded
                  color="#5CBBF6"
                  @click="login"
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
    </v-content>
    <v-footer app color="primary lighten-1" padless>
      <v-col class="primary lighten-2 py-1 text-center white--text" cols="12">
        {{ new Date().getFullYear() }} — Vuetify
      </v-col>
    </v-footer>
    <v-snackbar
      v-model="snackbar2"
      :multi-line="multiLine"
      shaped
      top
      centered
      color="#FF5252"
      dark
    >
      <h3>Credenciales invalidas</h3>

      <template v-slot:action="{ attrs }">
        <v-btn
          v-bind="attrs"
          @click="snackbar2 = false"
          class="ma-2"
          text
          icon
          color="white"
        >
          <v-icon large>mdi-close-circle</v-icon>
        </v-btn>
      </template>
    </v-snackbar>
  </v-app>
</template>
<script lang="ts">
import axios from "axios";
import VueCookies from "vue-cookies";
export default {
  data() {
    return {
      show1: false,
      valid: false,
      show2: true,
      snackbar2: false,
      men: "",
      email: "",
      loading: false,
      password: "",
      Password: "Password",
      rules: {
        required: (value: any) => !!value || "Campo requerido",
        min: (v: string | any[]) => v.length >= 8 || "Minimo 8 caracteres",
        emailMatch: () => `The email and password you entered don't match`,
        emailValido: (v: string) =>
          /.+@.+\..+/.test(v) || "Correo electrónico inválido",
      },
    };
  },
  /*esta funcion sirve para traer informacion del veterinario*/
  /*async asyncData() {
    try {
      const respuesta = await fetch(
        "http://localhost:8080/xampp/axios/api/prueba.php"
      );
      const post = await respuesta.json();
      console.log(post);

      return { veterinarios: post };
    } catch (error) {
      console.log(error);
      return { veterinarios: [] };
    }
  },*/

  methods: {
    eliminarCookie() {
      document.cookie =
        "Veterinario=" + "=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
      //this.$cookies.set("username", "gowtham");
    },
    /*checkCookie() {
      const cookies = document.cookie.split("; ");
      for (let i = 0; i < cookies.length; i++) {
        const cookie = cookies[i].split("=");
        if (cookie[0] === "XD") {
          console.log("La cookie existe"); // La cookie existe
        }
      }
      console.log("NO existe");
    },*/
    login() {
      axios
        .get("http://localhost:8080/xampp/axios/api/login.php", {
          params: {
            email_veterinario: this.email,

            password_veterinario: this.password,
          },
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log(response.data);

          if (response.data.toString() === "XD") {
            console.log("incorrecto");
            this.snackbar2 = true;
          } else {
            document.cookie = "Veterinario=" + response.data;
            // document.cookie = ("username=" response.data.toString());
            this.$router.push("XD/principal");
          }
          //this.$router.push("XD/principal");*/
        })
        .catch((error) => {
          console.log(error.data);
        });
    },
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
.no-scroll {
  overflow: hidden;
}
</style>

function delete_cookie() {
  throw new Error('Function not implemented.');
}
