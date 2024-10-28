<template>
  <v-app>

    <v-main>
  
 
      <NavBar />
        <IndexSection />
        <AboutSection />
        <PortfolioSection />
        <ContactSection />
    </v-main>

  </v-app>
</template>

<script>

import NavBar from './components/NavBar.vue'
import IndexSection from './components/IndexSection.vue'
import AboutSection from './components/AboutSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ContactSection from './components/ContactSection.vue'


export default {
  name: 'App',
  components: {
    
 
    NavBar,
    IndexSection,
    AboutSection,
    PortfolioSection,
    ContactSection,
  
   
  }
}

</script>
