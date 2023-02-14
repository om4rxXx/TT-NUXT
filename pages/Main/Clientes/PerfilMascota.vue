<template>
  <v-app>
    <nav-l></nav-l>
    <v-container class="pt-12">
      <v-card flat>
        <v-toolbar color="#5CBBF6" class="rounded-pill" app>
          <v-avatar class="px-3">
            <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
          </v-avatar>

          <v-toolbar-title class="ml-3 white--text"
            >Jesus palafox</v-toolbar-title
          >
        </v-toolbar>
      </v-card>
      <v-row>
        <v-col sm="8" md="8" lg="8">
          <v-card class="mx-auto rounded-xl" height="235">
            <v-row class="ma-5 py-12"
              ><v-col sm="3" md="3">
                <v-avatar size="90">
                  <img
                    src="https://www.hospitalveterinariglories.com/wp-content/uploads/2022/01/26-01-22-American-Bully-conoce-esta-raza-de-perro-.jpg"
                    alt="John"
                  /> </v-avatar
              ></v-col>
              <v-col sm="4" md="4">
                <v-list lines="one" density="compact"
                  ><v-list-item>
                    <v-list-item-content>
                      <v-list-item-title><h3>Pochita</h3></v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                  <v-list-item>
                    <v-list-item-content>
                      <v-list-item-title>Especie: Canino</v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </v-list></v-col
              ><v-col sm="5" md="5">
                <v-list lines="one" density="compact"
                  ><v-list-item>
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
              ></v-row
            >
          </v-card>
        </v-col>
        <v-col sm="4" md="4" lg="4">
          <v-card class="rounded-xl mx-auto my-5" height="235">
            <v-card-title>Datos</v-card-title>
            <v-card-text>
              <v-row>
                <v-col sm="8" md="8" lg="8">
                  <v-list lines="one" density="compact" class="pl-5">
                    <p>Edad:</p>
                    <p>Raza</p>
                    <p>Padecimientos:</p>
                    <p>Sexo:</p>
                  </v-list>
                </v-col>
                <v-col class="d-flex justify-end" sm="4" md="4" lg="4">
                  <v-list lines="one" density="compact" class="pr-3">
                    <p>15</p>
                    <p>Lobito</p>
                    <p>Ninguno</p>
                    <p>Macho</p>
                  </v-list>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <v-card color="basil">
        <v-card-title class="text-center justify-center py-6">
          <h1 class="font-weight-bold text-h2 basil--text">BASiL</h1>
        </v-card-title>

        <v-tabs v-model="tab" background-color="transparent" color="basil" grow>
          <v-tab v-for="item in items" :key="item">
            {{ item }}
          </v-tab>
        </v-tabs>

        <v-tabs-items v-model="tab">
          <v-tab-item v-for="item in items" :key="item">
            <v-card color="basil" flat>
              <v-card-text>{{ text }}</v-card-text>
            </v-card>
          </v-tab-item>
        </v-tabs-items>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      tab: null,
      items: ["Appetizers", "Entrees", "Deserts", "Cocktails"],
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
    };
  },
};
</script>

<style></style>
