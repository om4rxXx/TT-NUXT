<template>
  <v-app>
    <v-app-bar
      app
      color="#5CBBF6"
      dark
      class="mx-3 my-1 rounded-pill"
      elevation="10"
    >
      <v-avatar class="px-3">
        <img src="~/assets/images/logito.png" alt="John" />
      </v-avatar>

      <v-toolbar-title class="ml-3">Mr Can</v-toolbar-title>
    </v-app-bar>

    <main color="#5CBBF6">
      <v-row class="d-flex justify-center">
        <v-col cols="10">
          <v-card
            elevation="14"
            rounded="200"
            class="my-16 rounded-xl"
            color="white"
          >
            <v-card-text>
              <div>
                <p class="text-h4 text-color d-flex justify-start">Registro</p>
              </div>
              <div class="d-flex justify-center">
                <v-form>
                  <v-container>
                    <v-row>
                      <v-col cols="12" sm="6" md="6" lg="6">
                        <v-text-field
                          v-model="Nombre"
                          label="Nombre"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                          rounded
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6" md="6" lg="6">
                        <v-text-field
                          v-model="Apellido"
                          label="Apellido"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                          rounded
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="Telefono"
                          label="Telefono"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required, rules.min]"
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="email"
                          label="E-mail"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.emailValido]"
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="estado"
                          label="Estado"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="Ciudad"
                          label="Ciudad"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="Colonia"
                          label="Colonia"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                        ></v-text-field>
                      </v-col>

                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="postal"
                          label="C.P."
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="calle"
                          label="Calle"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          v-model="numeroE"
                          label="Numero Exterior"
                          outlined
                          dense
                          color="primary"
                          :rules="[rules.required]"
                        ></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-text-field
                          rounded
                          max-width="20"
                          v-model="Password"
                          label="Contraseña"
                          outlined
                          dense
                          :type="show1 ? 'text' : 'password'"
                          :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                          @click:append="show1 = !show1"
                          color="primary"
                          :rules="[rules.contraseñaSegura, rules.required]"
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
                  rounded
                  @click="CrearVeterinario"
                  :disabled="!formularioCompleto"
                >
                  Crear
                </v-btn>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </main>
  </v-app>
</template>
<script lang="ts">
import axios from "axios";
import moment from "moment";
export default {
  data() {
    return {
      show1: false,
      show2: true,
      Nombre: "",
      Apellido: "",
      password: "Password",
      Telefono: "",
      email: "",
      estado: "",
      Ciudad: "",
      Colonia: "",
      postal: "",
      calle: "",
      numeroE: "",
      Password: "",
      //password: "Password",
      rules: {
        required: (value: any) => !!value || "Campo requerido",
        min: (v: string | any[]) => v.length >= 10 || "Minimo 10 digitos",
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
      return (
        this.Nombre &&
        this.Apellido &&
        this.Telefono &&
        this.email &&
        this.estado &&
        this.Ciudad &&
        this.Colonia &&
        this.postal &&
        this.calle &&
        this.numeroE &&
        this.Password
      );
    },
  },
  methods: {
    CrearVeterinario() {
      axios
        .post("http://localhost:8080/xampp/axios/api/CrearVeterinario.php", {
          nombre_veterinario: this.Nombre,
          apellido_veterinario: this.Apellido,
          telefono_veterinario: parseInt(this.Telefono),
          email_veterinario: this.email,
          estado_veterinario: this.estado,
          ciudad_veterinario: this.Ciudad,
          colonia_veterinario: this.Colonia,
          cp_veterinario: parseInt(this.postal),
          calle_veterinario: this.calle,
          num_ext_veterinario: this.numeroE,
          password_veterinario: this.Password,
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log("Exitoso", response.data);
          this.$router.push("/");

          //window.location.reload();
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
