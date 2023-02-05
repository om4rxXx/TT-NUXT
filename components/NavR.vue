<template>
  <v-navigation-drawer permanent app right>
    <v-img
      height="200"
      src="https://ddragon.leagueoflegends.com/cdn/img/champion/splash/Mordekaiser_0.jpg"
    ></v-img>

    <v-divider class="mx-4"></v-divider>

    <v-list dense nav>
      <v-list-item class="md-4">
        <v-list-item-content>
          <v-list-item-title><h2>Contacto</h2></v-list-item-title>
        </v-list-item-content>
        <v-list-item-icon>
          <v-btn icon to="/Main/Perfil">
            <v-icon>mdi-pencil</v-icon>
          </v-btn>
        </v-list-item-icon>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-account-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Veterinario</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-phone-classic</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>+52 468191589</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-email-fast-outline</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Veterinario@gmail.com</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title><h2>Información adicional</h2></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-calendar-badge-outline</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>11</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-account-supervisor-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>80 clientes</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-map-marker</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title
            >Zacatecas, Zacatecas, San Pedro 102</v-list-item-title
          >
        </v-list-item-content>
      </v-list-item>
      <v-list-item>
        <v-list-item-icon>
          <v-icon>mdi-account-supervisor-circle</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>Usuarios</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  name: "NavR",
};
</script>

<style></style>
