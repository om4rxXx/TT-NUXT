<template>
  <v-app>
    <nav-l></nav-l>
    <v-container class="pt-12 px-15">
      <v-card flat>
        <v-toolbar color="#5CBBF6" class="mx-3 my-1 rounded-pill" flat>
          <v-avatar class="px-3">
            <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
          </v-avatar>

          <v-toolbar-title class="ml-3 white--text">Mr Can</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-col md="4" sm="4" lg="4">
            <v-text-field
              class="pt-8"
              v-model="search"
              label="Buscar"
              solo
              append-icon="mdi-magnify"
              rounded
            ></v-text-field>
          </v-col>
        </v-toolbar>
      </v-card>
      <div class="pt-12">
        <v-card elevation="14" class="rounded-xl">
          <v-data-table
            :headers="headers"
            :items="desserts"
            item-key="name"
            class="elevation-1"
            :search="search"
            elevation="14"
          >
          </v-data-table>
        </v-card>
      </div>
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
      search: "",

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
      ],
    };
  },
  computed: {
    headers() {
      return [
        {
          text: "Nombre",
          align: "start",
          sortable: false,
          value: "name",
        },

        {
          text: "Estado de Solicitud",
          align: "Center",
          value: "verified",
          sortable: false,
          value: "name",
        },
        {
          text: "Mascotas",
          align: "Center",
          sortable: false,
          value: "name",
        },

        {
          text: "Dar de baja",
          align: "Center",
          sortable: false,
          value: "name",
        },
      ];
    },
  },
  methods: {
    filterOnlyCapsText(value, search, item) {
      return (
        value != null &&
        search != null &&
        typeof value === "string" &&
        value.toString().toLocaleUpperCase().indexOf(search) !== -1
      );
    },
  },
};
</script>

<style></style>
