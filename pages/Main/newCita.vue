<template>
  <v-app>
    <nav-l></nav-l>

    <v-container>
      <h2 class="py-7"></h2>

      <v-card flat rounded="xl" elevation="2" outlined
        ><div><p></p></div>
        <div class="d-flex justify-center">
          <v-card-title>Agendar Cita</v-card-title>
        </div>
        <v-form>
          <v-container>
            <v-row>
              <v-col sm="6" md="6"
                ><div class="text-center pl-12">
                  <v-card flat>
                    <v-row class="pb-5">
                      <v-col sm="3" md="3">
                        <v-avatar size="90">
                          <img
                            src="https://www.hospitalveterinariglories.com/wp-content/uploads/2022/01/26-01-22-American-Bully-conoce-esta-raza-de-perro-.jpg"
                            alt="John"
                          /> </v-avatar
                      ></v-col>
                      <v-col sm="4" md="4">
                        <v-list dense nav>
                          <v-list-item>
                            <v-list-item-content>
                              <v-list-item-title
                                ><h3>Pochita</h3></v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                          <v-list-item>
                            <v-list-item-content>
                              <v-list-item-title
                                >Especie: Canino</v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                        </v-list></v-col
                      >
                      <v-col sm="5" md="5">
                        <v-list dense nav>
                          <v-list-item>
                            <v-list-item-content>
                              <v-list-item-title
                                >Nacimiento: 12/06/2022</v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                          <v-list-item>
                            <v-list-item-content>
                              <v-list-item-title
                                >Dueño: Jesus Palafox</v-list-item-title
                              >
                            </v-list-item-content>
                          </v-list-item>
                        </v-list></v-col
                      >
                    </v-row>
                  </v-card>

                  <v-select
                    :items="items"
                    label="Motivo"
                    outlined
                    chips
                  ></v-select>
                  <v-text-field
                    dense
                    label="Descripcion"
                    outlined
                  ></v-text-field>
                  <v-text-field
                    dense
                    label="Observaciones"
                    outlined
                  ></v-text-field>
                  <v-select
                    :items="items"
                    label="Motivo"
                    outlined
                    chips
                  ></v-select></div
              ></v-col>
              <v-col sm="6" md="6">
                <div class="d-flex justify-center">
                  <v-date-picker
                    class="rounded-xl"
                    dark
                    locale="spanish"
                    v-model="picker"
                    elevation="15"
                  ></v-date-picker>
                </div>
              </v-col>
            </v-row>
          </v-container>
          <div class="d-flex justify-center">
            <v-btn
              height="50"
              class="btn-center white--text rounded-xl ma-6"
              depressed
              color="#5C0FD9"
              :loading="loading"
              @click="editarUser"
              to="/Main/Main"
            >
              Agendar
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

  data: () => ({
    items: ["Vacunacion", "Medica", "Estetica", "Buzz"],
  }),
  data() {
    return {
      picker: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
        .toISOString()
        .substr(0, 10),
    };
  },
};
</script>

<style></style>
