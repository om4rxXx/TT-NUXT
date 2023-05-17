<template>
  <v-app>
    <nav-l></nav-l>

    <v-container class="mx-0">
      <h2 class="py-7">Información personal</h2>
      <v-row>
        <v-card elevation="14" class="rounded-xl" outlined width="1800">
          <v-form class="pt-5 pl-2">
            <v-container>
              <v-row class="d-flex justify-center">
                <v-col sm="4" md="4">
                  <v-text-field
                    rounded
                    v-model="Nombre"
                    :label="veterinario.nombre_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>

                  <v-text-field
                    rounded
                    v-model="Telefono"
                    :label="veterinario.telefono_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>

                  <v-text-field
                    rounded
                    v-model="Estado"
                    :label="veterinario.estado_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>
                  <v-text-field
                    rounded
                    v-model="Colonia"
                    :label="veterinario.colonia_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>
                  <v-text-field
                    rounded
                    v-model="Calle"
                    :label="veterinario.calle_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>
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
                    class="py-2"
                    :rules="[rules.contraseñaSegura]"
                  ></v-text-field>
                </v-col>
                <v-col sm="4" md="4">
                  <v-text-field
                    rounded
                    v-model="Apellido"
                    :label="veterinario.apellido_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>

                  <v-text-field
                    rounded
                    v-model="Email"
                    :label="veterinario.email_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                    :rules="[rules.emailValido]"
                  ></v-text-field>
                  <v-text-field
                    rounded
                    v-model="Ciudad"
                    :label="veterinario.ciudad_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>
                  <v-text-field
                    rounded
                    v-model="Postal"
                    :label="veterinario.cp_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>
                  <v-text-field
                    rounded
                    v-model="NumeroE"
                    :label="veterinario.num_ext_veterinario"
                    outlined
                    dense
                    color="primary"
                    class="py-2"
                  ></v-text-field>
                </v-col>
                <v-col sm="4" md="4">
                  <div class="d-flex justify-center">
                    <v-card width="300" class="rounded-xl" elevation="7">
                      <template v-if="veterinario.foto_veterinario">
                        <v-img
                          height="150"
                          :src="
                            'data:image/png;base64,' +
                            veterinario.foto_veterinario
                          "
                          alt="John"
                        ></v-img>
                      </template>
                      <template v-else>
                        <v-img
                          src="https://picsum.photos/350/165?random"
                          height="150"
                        ></v-img
                      ></template>

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
                              v-model="selectedFile"
                              label="Seleccionar archivo"
                              :rules="img"
                              accept="image/png, image/jpeg, image/bmp"
                              prepend-icon="mdi-pencil"
                            ></v-file-input>
                          </v-list-item-icon>
                        </v-list-item>
                        <div class="d-flex justify-center">
                          <v-btn
                            color="#5CBBF6"
                            class="btn-center white--text rounded-xl ma-6"
                            @click="convertAndLogBase64"
                            >subir foto</v-btn
                          >
                        </div></v-list
                      >
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
                @click="editarVeterinario"
              >
                Guardar
              </v-btn>
              <v-btn
                height="50"
                class="btn-center white--text rounded-xl ma-6"
                depressed
                color="#FF5252"
                to="/XD/Principal"
              >
                Cancelar
              </v-btn>
            </div>
          </v-form>
        </v-card>
      </v-row>
      <v-snackbar
        v-model="snackbar2"
        :multi-line="multiLine"
        shaped
        top
        centered
        color="success"
        dark
      >
        <h3>Editado correctamente</h3>

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
    </v-container>
  </v-app>
</template>

<script lang="ts">
import axios from "axios";
import moment from "moment";
import { component } from "vue/types/umd";
import NavL from "~/components/NavL.vue";
import NavR from "~/components/NavR.vue";
export default {
  components: {
    NavL,
    NavR,
  },
  data() {
    return {
      passwordSecurity: {
        text: "",
        color: "",
        textColor: "",
      },
      show1: false,
      show2: false,
      snackbar2: false,
      Nombre: "",
      Telefono: "",
      imageSrc: null,
      selectedFile: null,
      Estado: "",
      Colonia: "",
      Calle: "",
      Password: "",
      Apellido: "",
      Email: "",
      Ciudad: "",
      Postal: "",
      NumeroE: "",
      bytes: null,

      password: "Password",
      color: "",
      veterinario: [],
      fileData: null,
      rules: {
        min: (v: string | any[]) => v.length >= 8 || "Minimo 8 caracteres",
        emailMatch: () => `The email and password you entered don't match`,
        emailValido: (v: string) =>
          /.+@.+\..+/.test(v) || "Correo electrónico inválido",
        contraseñaSegura: (v: string) => {
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
  mounted() {
    // traer datos de consulta
    axios
      .get("http://localhost:8080/xampp/axios/api/veterinario.php", {})
      .then((response) => {
        this.veterinario = response.data;
        console.log(response.data);
      })
      .catch((error) => {
        console.error(error);
      });
    const existe = this.checkCookie();
    if (existe) {
      console.log("La cookie existe");
    } else {
      this.$router.push("/");
    }
  },
  methods: {
    convertToBase64(file: Blob | null) {
      return new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onload = () => {
          const base64 = btoa(reader.result);
          resolve(base64);
        };
        reader.onerror = (error) => {
          reject(error);
        };
        reader.readAsBinaryString(file);
      });
    },
    async convertAndLogBase64() {
      const base64 = await this.convertToBase64(this.selectedFile);
      console.log(base64);

      axios
        .post("http://localhost:8080/xampp/axios/api/enviarfoto.php", {
          foto_veterinario: base64,
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log("Exitoso", response.data);

          //window.location.reload();
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },
    checkCookie() {
      const cookies = document.cookie.split("; ");
      for (let i = 0; i < cookies.length; i++) {
        const cookie = cookies[i].split("=");
        if (cookie[0] === "Veterinario") {
          return true; // La cookie existe
        }
      }
      return false; // La cookie no existe
    },

    editarVeterinario() {
      axios
        .get("http://localhost:8080/xampp/axios/api/editarVeterinario.php", {
          params: {
            nombre_veterinario: this.Nombre,
            apellido_veterinario: this.Apellido,
            telefono_veterinario: this.Telefono,
            email_veterinario: this.Email,
            estado_veterinario: this.Estado,
            ciudad_veterinario: this.Ciudad,
            colonia_veterinario: this.Colonia,
            cp_veterinario: this.Postal,
            calle_veterinario: this.Calle,
            num_ext_veterinario: this.NumeroE,
            password_veterinario: this.Password,
          },
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log("Exitoso", response.data.foto_veterinario);

          this.snackbar2 = true;
          setTimeout(() => {
            this.$router.push("principal");
          }, 5000);

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

<style></style>
