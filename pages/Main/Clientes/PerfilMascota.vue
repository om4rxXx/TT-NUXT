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
        <v-col sm="8" md="8" lg="8" xl="8">
          <v-card class="rounded-xl" height="235">
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
      <v-card class="mx-auto rounded-xl">
        <v-card-title class="text-center justify-center py-6">
          <h1 class="font-weight-bold text-h2 basil--text">BASiL</h1>
        </v-card-title>

        <v-tabs v-model="tab" grow>
          <v-tab v-for="item in items" :key="item">
            {{ item }}
          </v-tab>
        </v-tabs>

        <v-tabs-items v-model="tab">
          <v-tab-item v-for="item in items" :key="item">
            <v-card color="basil" flat>
              <v-card-text>
                <v-data-table
                  :headers="headers"
                  :items="desserts"
                  :items-per-page="5"
                ></v-data-table>
              </v-card-text>
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
      items: ["Medica", "Vacunacion"],
      headers: [
        {
          text: "Dessert (100g serving)",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "Calories", value: "calories" },
        { text: "Fat (g)", value: "fat" },
        { text: "Carbs (g)", value: "carbs" },
        { text: "Protein (g)", value: "protein" },
        { text: "Iron (%)", value: "iron" },
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: 1,
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: 1,
        },
        {
          name: "Eclair",
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: 7,
        },
        {
          name: "Cupcake",
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: 8,
        },
        {
          name: "Gingerbread",
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: 16,
        },
        {
          name: "Jelly bean",
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: 0,
        },
        {
          name: "Lollipop",
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: 2,
        },
        {
          name: "Honeycomb",
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: 45,
        },
        {
          name: "Donut",
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: 22,
        },
        {
          name: "KitKat",
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: 6,
        },
      ],
    };
  },
};
</script>

<style></style>
