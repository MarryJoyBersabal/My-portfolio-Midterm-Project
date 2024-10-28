<template>
  <div>
    <v-app-bar app flat class="nav-bar px-4" elevation="0">
      <v-app-bar-nav-icon 
        @click.stop="drawer = !drawer" 
        class="d-md-none burger-icon"
        color="white"
      ></v-app-bar-nav-icon>
      
      <v-app-bar-title class="nav-brand">
        <router-link to="/" class="text-decoration-none brand-text">
          <span class="brand-first">Bersabal</span>
          <span class="brand-dot">.</span>
          <span class="brand-last">M</span>
        </router-link>
      </v-app-bar-title>
      
      <v-spacer></v-spacer>

      <!-- Desktop Navigation -->
      <div class="d-none d-md-flex align-center">
        <v-btn 
          v-for="(item, index) in menuItems"
          :key="index"
          text
          class="nav-btn mx-2"
          @click="scrollTo(item.section)"
        >
          <v-icon small class="mr-1" color="white">{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>
      </div>
    </v-app-bar>

    <!-- Mobile Navigation Drawer -->
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
      right
      class="custom-drawer"
      width="280"
    >
      <div class="drawer-header pa-4">
        <span class="text-h6">Menu</span>
        <v-btn icon @click="drawer = false">
          <v-icon>mdi-close</v-icon>
        </v-btn>
      </div>
      
      <v-divider></v-divider>
      
      <v-list nav>
        <v-list-item
          v-for="(item, index) in menuItems"
          :key="index"
          link
          class="drawer-item my-2"
          @click="handleItemClick(item.section)"
        >
          <v-list-item-icon>
            <v-icon :color="FFA500">{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      drawer: false,
      menuItems: [
        { title: 'Home', section: '#index', icon: 'mdi-home' },
        { title: 'About', section: '#about', icon: 'mdi-account' },
        { title: 'Portfolio', section: '#portfolio', icon: 'mdi-briefcase' },
        { title: 'Contact', section: '#contact', icon: 'mdi-phone' }
      ]
    };
  },
  methods: {
    scrollTo(section) {
      const element = document.querySelector(section);
      if (element) {
        element.scrollIntoView({ 
          behavior: 'smooth',
          block: 'start'
        });
      }
    },
    handleItemClick(section) {
      this.scrollTo(section);
      this.drawer = false;
    }
  }
};
</script>

<style scoped>
.nav-bar {
  background-color: #1a1a1a !important;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.nav-brand {
  font-family: 'Poppins', sans-serif;
  letter-spacing: 1px;
}

.brand-text {
  font-size: 1.5rem;
  font-weight: 600;
}

.brand-first {
  color: white;
}

.brand-dot {
  color: #FFA500;
}

.brand-last {
  color: white;
  font-weight: 300;
}

.nav-btn {
  position: relative;
  color: #FFA500 !important;
  font-weight: 500;
  letter-spacing: 0.5px;
  padding: 0 20px;
  height: 40px;
  transition: all 0.3s ease;
}

.nav-btn::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 0;
  height: 2px;
  background-color: #FFA500;
  transition: all 0.3s ease;
  transform: translateX(-50%);
}

.nav-btn:hover::after {
  width: 80%;
}

.nav-btn:hover {
  transform: translateY(-2px);
}

.custom-drawer {
  background-color: #1a1a1a !important;
}

.drawer-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #1a1a1a;
}

.drawer-header .text-h6 {
  color: white;
  font-weight: 500;
}

.drawer-item {
  margin: 8px 16px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.drawer-item:hover {
  background-color: rgba(255, 165, 0, 0.1) !important;
}

.v-list-item-title {
  color: white !important;
  font-weight: 500;
  letter-spacing: 0.5px;
}

.burger-icon::before {
  color: white !important;
}

/* Animation for mobile menu items */
.v-list-item {
  transform: translateX(0);
  transition: transform 0.3s ease;
}

.v-list-item:hover {
  transform: translateX(10px);
}

/* Responsive adjustments */
@media (max-width: 600px) {
  .nav-brand {
    font-size: 1.2rem;
  }
}
</style>