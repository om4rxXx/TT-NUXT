<template>
  <v-navigation-drawer permanent app>
    <v-list-item link to="/Main/Perfil">
      <v-list-item-content>
        <v-list-item-title class="text-h6">
          <v-avatar class="px-3 mr-2">
            <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
          </v-avatar>
          Veterinario
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-divider></v-divider>

    <v-list dense nav>
      <v-list-item link to="/Main/Main">
        <v-list-item-icon>
          <v-icon>mdi-calendar-clock-outline</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title><h3>Citas</h3></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item link to="/Main/Users">
        <v-list-item-icon>
          <v-icon>mdi-account-supervisor-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title><h3>Usuarios</h3></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <template v-slot:append>
      <v-list-item link>
        <v-list-item-icon>
          <v-icon>mdi-logout</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Cerrar sesión</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </template>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: "NavL",
};
</script>

<style></style>
