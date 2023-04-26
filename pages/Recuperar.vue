<template>
  <v-app>
    <v-app-bar app color="#5CBBF6" dark class="mx-3 my-1 rounded-pill" flat>
      <v-avatar class="px-3">
        <img src="~/assets/images/logito.png" alt="John" />
      </v-avatar>

      <v-toolbar-title class="ml-3">Mr Can</v-toolbar-title>
    </v-app-bar>
    <v-content>
      <v-row class="d-flex justify-center no-scroll">
        <v-col cols="8">
          <v-card
            elevation="14"
            rounded="200"
            height="600"
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
                  ¿Olvidaste la contraseña?
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
                </v-form>
              </div>

              <p></p>
              <p></p>
              <p></p>
              <div class="d-flex justify-center">
                <v-btn
                  min-width="300"
                  min-height="50"
                  class="btn-center white--text my-13"
                  depressed
                  color="#3D76F2"
                  rounded
                  @click="mail"
                  :disabled="!formularioCompleto"
                >
                  Enviar contraseña
                </v-btn>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>

      <v-snackbar
        v-model="snackbar1"
        :multi-line="multiLine"
        shaped
        top
        centered
        color="#5C0FD9"
        dark
      >
        <h3>{{ text }}</h3>

        <template v-slot:action="{ attrs }">
          <v-btn
            v-bind="attrs"
            @click="snackbar1 = false"
            class="ma-2"
            text
            icon
            color="white"
          >
            <v-icon large>mdi-close-circle</v-icon>
          </v-btn>
        </template>
      </v-snackbar>
    </v-content>
  </v-app>
</template>
<script lang="ts">
import axios from "axios";
import moment from "moment";
import { component } from "vue/types/umd";
export default {
  data() {
    return {
      multiLine: true,
      snackbar1: false,

      text: `se enviaron sus datos al correo`,

      password: "",
      email: "",
      correo: "",
      contra: "",
      rules: {
        min: (v: string | any[]) => v.length >= 8 || "Minimo 8 caracteres",
        emailMatch: () => `The email and password you entered don't match`,
        emailValido: (v) =>
          /.+@.+\..+/.test(v) || "Correo electrónico inválido",
        contraseñaSegura: (v) => {
          if (!v) {
            return true; // No hay contraseña para validar
          }

          const hasLength = v.length >= 8;
          const hasNumber = /\d/.test(v);
          const hasUpper = /[A-Z]/.test(v);
          const hasLower = /[a-z]/.test(v);
          const hasSpecial = /[$@!%*?&]/.test(v);

          return (
            (hasLength && hasNumber && hasUpper && hasLower && hasSpecial) ||
            "La contraseña debe tener al menos 8 caracteres, una letra mayúscula, una letra minúscula, un número y un carácter especial ($@!%*?&)"
          );
        },
      },
    };
  },
  computed: {
    formularioCompleto() {
      return this.email;
    },
  },
  methods: {
    myFunction(id) {
      this.$router.push(id + "/principal");
    },
    mail() {
      axios
        .post("http://localhost:8080/xampp/axios/api/enviar_mail.php", {
          email_veterinario: this.email,
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          this.correo = response.data.email_veterinario;
          this.contra = response.data.password_veterinario;
          //window.location.reload();
          console.log(response.data);

          axios
            .post("http://localhost:8080/mail/", {
              correo: this.email,
              password: this.contra,
            })
            .then((response) => {
              // Manejar la respuesta exitosa
              //window.location.reload();
              this.snackbar1 = true;

              console.log(response.data);
            })
            .catch((error) => {
              // Manejar el error
              console.error(error);
            });
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
.text-color {
  color: #3d76f2;
}
.v-text-field {
  width: 400px;
}
</style>
