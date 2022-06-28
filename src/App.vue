<template>
  <v-app id="inspire">
   <v-navigation-drawer 
     v-model="drawer"
     dark
     src="https://st2.depositphotos.com/1288351/5862/i/600/depositphotos_58628561-stock-photo-night-sky-praise.jpg"
     app>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Usuario
          </v-list-item-title>
          <v-list-item-subtitle>
            usuario@gmail.com
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
	        :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app
         dark
         src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar
          dark
          src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg">
        <v-toolbar-title>TechFind</v-toolbar-title>
      </v-toolbar>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
       drawer: null,
       items: [
          { title: 'Main Page', icon: 'mdi-view-dashboard', to: '/' },
          { title: 'Vendedor', icon: 'mdi-currency-usd', to: '/vendedor' },
          { title: 'Colaboradores', icon: 'mdi-help-box', to: '/colaboradores'  },
          { title: 'Usuario', icon: 'mdi-account', to: '/user' },
          { title: 'Producto', icon: 'mdi-tooltip-text', to: '/producto' },
          { title: 'Catálogo', icon: 'mdi-tooltip-text', to: '/catalogo' },
          { title: 'Login', icon: 'mdi-tooltip-text', to: '/Login' }
        ],
      }),
  }
</script>