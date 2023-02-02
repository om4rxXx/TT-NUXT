<template >
<div >
  <v-app >
    <v-navigation-drawer permanent app>
      <v-list-item link>
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
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-calendar-clock-outline</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title><h3>Citas</h3></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
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
    <!-------- naveacion derecha-->
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
            <v-btn icon>
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
            <v-list-item-title
              ><h2>Información adicional</h2></v-list-item-title
            >
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
    <!--central-->
    <main >
      <v-container >
        <h2 class="py-7">Citas pendientes </h2>
        <v-row>
          
          
        <v-col
          cols="12"
          sm="6"
          md="4"
        >
      <v-card
    flat rounded="xl"
    outlined
    min-height="204.8"
  ><v-list-item three-line>
      <v-list-item-content>
        
        <v-list-item-title class="text-h5 mb-1">
          Medica
        </v-list-item-title>
        <v-list-item class="md-4">
          <v-list-item-content>
            <v-list-item-title>Nombre:</v-list-item-title>
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title><h4>PEPE</h4></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item class="md-4">
          <v-list-item-content>
            <v-list-item-title>Raza:</v-list-item-title>
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title><h4>PEPE</h4></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item class="md-4">
          <v-list-item-content>
            <v-list-item-title><a
                    href="https://www.leagueoflegends.com/es-mx/"
                    class="text-decoration-none mr-10 pr-10"
                    >Detalles</a
                  ></v-list-item-title>
          </v-list-item-content>
          
        </v-list-item> 
      </v-list-item-content>
    </v-list-item>
  </v-card>
          </v-col>
          <v-col
          cols="12"
          sm="6"
          md="4"
        >
      <v-card
    flat rounded="xl"
    outlined
    min-height="204.8"
  ><v-list-item three-line>
      <v-list-item-content>
        
        <v-list-item-title class="text-h5 mb-1">
          Detalles
        </v-list-item-title>
        <v-list-item class="md-4">
          <v-list-item-content>
            <v-list-item-title>Se esta muriendo</v-list-item-title>
          </v-list-item-content>
         
        </v-list-item>
        
          </v-list-item-content>
          
        </v-list-item> 
      
  </v-card>
          </v-col>
          <v-col
          cols="12"
          sm="6"
          md="4"
        >
      <v-card
    flat rounded="xl"
    outlined
    min-height="204.8"
  >
  <v-card-title class="justify-center text-h5">Hora</v-card-title>
                
                <v-card-text class="justify-cente mt-4">
                  <div class="text-center ">
                    <v-btn icon depressed>
    <v-icon x-large>mdi-clock-time-four-outline</v-icon>
    <div><p class="text-h5" >10:30</p></div>
</v-btn>
                    
                  </div>
                  
                </v-card-text>
                 <v-card-text>
                  <div class="text-center">
                    <v-btn
      depressed
      color="#3D76F2"
      class="white--text"
    >
      Iniciar
    </v-btn>
                    
                  </div>
                </v-card-text>
                
  </v-card>
          </v-col>
          
        </v-row>
      </v-container>
    </main>
  </v-app>
</div>
</template>

<script>
export default {};
</script>

<style>
.v-btn__content {
    display:flex;
    flex-direction:column;
}

</style>
<!--<v-container v-if="!getStatusNextReservationsByUser">
    <div v-if="nextReservationsByUser.length > 0">
      <!--    <h1>Historial de viajes pasajero</h1> 
      <v-row
        v-for="(nextReservation, index) in nextReservationsByUser"
        :key="index"
      >
        <v-col>
          <h3>{{ nextReservation.date }}</h3>
          <v-row
            v-for="reservation in nextReservation.reservation"
            :key="reservation.id"
          >
            <v-col md="12" sm="12" xs="12" lg="12" xl="10">
              <v-card class="mt-6" flat rounded="xl">
                <v-list class="pl-4 pr-4">
                  <v-list-item>
                    <v-list-item-content>
                      <v-list-item-title class="font-weight-medium">
                        {{ moment(reservation.ride.date).format('h:mm a') }}
                      </v-list-item-title>
                    </v-list-item-content>

                    <v-list-item-action class="font-weight-medium ml-0">
                      ${{ reservation.ride.price }}
                    </v-list-item-action>
                  </v-list-item>
                </v-list>

                <v-card-text class="mt-0 pt-0 black--text font-weight-light">
                  <div class="rightbox">
                    <div class="rb-container">
                      <ul class="rb">
                        <li class="rb-item" ng-repeat="itembx">
                          <div class="item-title">
                            {{ reservation.origin_appointment.place.name }}
                          </div>
                        </li>
                        <li class="rb-item" ng-repeat="itembx">
                          <div class="item-title">
                            {{ reservation.destination_appointment.place.name }}
                          </div>
                        </li>
                      </ul>
                    </div>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="2" class="hidden-lg-and-down">
              <v-card flat rounded="xl" class="mt-6">
                <v-card-title class="justify-center">Conductor</v-card-title>
                <v-card-text class="justify-center">
                  <div class="text-center">
                    <v-avatar>
                      <img
                        :src="reservation.driver.profile_picture.url"
                        alt="John"
                      />
                    </v-avatar>
                  </div>
                </v-card-text>

                <v-card-text class="black--text font-weight-light">
                  <div class="text-center text-truncate">
                    {{ reservation.driver.name }}
                    {{ reservation.driver.lastname }}
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </div>
    <div v-else>
      <h1>No hay viajes como pasajero</h1>
    </div>
  </v-container>-->
        </div></v-container
      >
    </main></v-app
  >
</template>
