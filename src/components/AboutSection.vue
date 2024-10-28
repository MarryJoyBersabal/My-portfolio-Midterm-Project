<template>
  <v-container fluid class="about-section py-16" id="about">

    <!-- Animated Header with Typing Effect -->
    <v-row justify="center" align="center" class="text-center mb-12">
      <v-col cols="12" md="8">
        <h1 class="text-header mb-4">
          <span class="typing-text">{{ displayText }}</span>
          <span class="cursor">|</span>
        </h1>
        <div class="bio-text">
          <v-chip-group>
            <v-chip v-for="(role, index) in roles" :key="index" :color="roleColors[index]" variant="elevated"
              class="ma-2 role-chip">
              {{ role }}
            </v-chip>
          </v-chip-group>
        </div>
      </v-col>
    </v-row>

    <v-row class="mt-8">
      <!--  Profile Card -->
      <v-col cols="12" md="5">
        <v-hover v-slot="{ isHovering, props }">
          <v-card v-bind="props" :elevation="isHovering ? 12 : 2" class="profile-card glass-effect"
            :class="{ 'on-hover': isHovering }">
            <v-img src="@/assets/myme.jpg" height="500" cover class="profile-image">
              <template v-slot:placeholder>
                <v-row align="center" justify="center">
                  <v-progress-circular indeterminate color="orange"></v-progress-circular>
                </v-row>
              </template>

              <div class="image-overlay" v-if="isHovering">
                <v-btn v-for="(social, index) in socials" :key="index" :color="social.color" variant="text"
                  :icon="social.icon" class="mx-2" @click="openSocial(social.link)"></v-btn>
              </div>
        
            </v-img>
          </v-card>
        </v-hover>

        <!-- Timeline Section -->
    <div class="content-wrapper mb-8">
    <h3 class="text-header-sub mb-4">
      <v-icon color="orange" class="mr-2">mdi-timeline</v-icon>
      Experience
    </h3>
    
    <div class="timeline-container">
      <v-timeline align="start" class="timeline-custom">
        <v-timeline-item v-for="(exp, index) in experience" 
                        :key="index" 
                        :dot-color="exp.iconColor || 'orange'" 
                        size="small"
                        :elevation="2">
          <template v-slot:icon>
            <v-avatar class="timeline-icon-wrapper">
              <v-icon :color="exp.iconColor || 'orange'">{{ exp.icon }}</v-icon>
            </v-avatar>
          </template>
          
          <div class="timeline-content">
            <div class="timeline-period">
              <span class="period-chip">{{ exp.period }}</span>
            </div>
            
            <v-card class="timeline-card glass-effect">
              <div class="card-content">
                <div class="title-section">
                  <div class="position-tag">
                    <span class="position-text">{{ exp.title }}</span>
                  </div>
                  <div class="company-name">{{ exp.company }}</div>
                </div>
                
                <div class="description-section">
                  <div class="description-divider"></div>
                  <p class="description-text">{{ exp.description }}</p>
                </div>
              </div>
            </v-card>
          </div>
        </v-timeline-item>
      </v-timeline>
    </div>
  </div>
      </v-col>

      <!--  Content Section -->
      <v-col cols="12" md="7">
        <!-- Animated Bio Section -->
        <v-slide-y-transition>
          <div class="content-wrapper mb-8">
            <h2 class="text-header-sub mb-4">
              <v-icon color="orange" class="mr-2">mdi-account-circle</v-icon>
              Who am I?
            </h2>
            <v-expand-transition>
              <div class="bio-container">
                <p class="bio-text mb-4">
                  {{ bioText }}
                </p>

              </div>
            </v-expand-transition>
          </div>
        </v-slide-y-transition>

      

        <!--  Skills Section -->
        <v-slide-y-transition>
          <div class="content-wrapper">
            <h3 class="text-header-sub mb-4">
              <v-icon color="orange" class="mr-2">mdi-tools</v-icon>
              Technical Skills
            </h3>
            <v-row>
              <v-col v-for="(skill, index) in skills" :key="index" cols="6" sm="2" md="2">
                <v-hover v-slot="{ isHovering, props }">
                  <v-card v-bind="props" class="skill-card glass-effect" :class="{ 'on-hover': isHovering }">
                    <v-card-text class="text-center">
                      <v-img :src="skill.logo" :alt="skill.name" width="40" height="40" class="mx-auto mb-2"></v-img>
                      <div class="skill-name">{{ skill.name }}</div>
                      <v-progress-linear v-if="isHovering" :model-value="skill.level" color="orange"
                        height="4"></v-progress-linear>
                    </v-card-text>
                  </v-card>
                </v-hover>
              </v-col>
            </v-row>
          </div>
        </v-slide-y-transition>
          

        <!--  CTA Button -->
        <v-row class="mt-8">
          <v-col cols="12" class="text-center">
            <v-btn class="hire-btn" size="x-large" rounded="pill" elevation="4" @click="scrollToContact"
              :loading="loading">
              <v-icon start>mdi-handshake</v-icon>
              Let's Work Together
              <v-icon end>mdi-arrow-right</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'AboutSection',

  data: () => ({
    displayText: '',
    fullText: "Hello, I'm Marry Joy Bersabal",
    typing: true,
    expandBio: false,
    loading: false,
    roles: ['Full Stack Developer', 'UI/UX Enthusiast', 'Problem Solver'],
    roleColors: ['orange', 'deep-orange', 'amber'],
    socials: [
      { icon: 'mdi-github', link: 'https://github.com/', color: 'white' },
      { icon: 'mdi-linkedin', link: 'https://linkedin.com/', color: 'blue-lighten-1' },
      { icon: 'mdi-twitter', link: 'https://twitter.com/', color: 'light-blue' }
    ],
    bioText: "I'm a Full Stack Developer with a passion for creating innovative digital solutions. I specialize in building scalable web applications and crafting intuitive user experiences.",
    experience: [
      {
        title: 'Full Stack Developer',
        company: 'College Of Computing and Information Sciences',
        period: '2024 - Present',
        icon: 'mdi-laptop',
        description: 'Leading development of enterprise web applications using modern technologies.'
      },
      {
        title: 'App Developer',
        company: 'Jabez Digital Agency',
        period: '2020 - 2022',
        icon: 'mdi-cellphone',
        description: 'Developed mobile applications and implemented responsive designs.'
      },
      {
        title: 'Graphics Designer',
        company: 'Gen Touch Company',
        period: '2019 - 2020',
        icon: 'mdi-palette',
        description: 'Created visual designs and branding materials for clients.'
      }
    ],
    skills: [
      { name: 'HTML', logo: require('@/assets/img/logos/html.png'), level: 95 },
      { name: 'CSS', logo: require('@/assets/img/logos/css.png'), level: 90 },
      { name: 'Bootstrap', logo: require('@/assets/img/logos/bootstrap.png'), level: 85 },
      { name: 'JavaScript', logo: require('@/assets/img/logos/javascript.png'), level: 88 },
      { name: 'Java', logo: require('@/assets/img/logos/java.png'), level: 80 },
      { name: 'Laravel', logo: require('@/assets/img/logos/laravel.png'), level: 85 },
      { name: 'PHP', logo: require('@/assets/img/logos/php.png'), level: 82 },
      { name: 'SQL', logo: require('@/assets/img/logos/sql.png'), level: 87 },
      { name: 'Supabase', logo: require('@/assets/img/logos/supabase.png'), level: 75 },
      { name: 'Vue.js', logo: require('@/assets/img/logos/vue.png'), level: 92 },
      { name: 'Vuetify', logo: require('@/assets/img/logos/vuetify.png'), level: 88 }
    ]
  }),

  mounted() {
    this.typeText()
  },

  methods: {
    async typeText() {
      let i = 0
      while (this.typing) {
        if (i < this.fullText.length) {
          this.displayText = this.fullText.slice(0, i + 1)
          i++
          await this.wait(100)
        } else {
          await this.wait(2000)
          i = 0
        }
      }
    },

    wait(ms) {
      return new Promise(resolve => setTimeout(resolve, ms))
    },

    scrollToContact() {
      this.loading = true
      const element = document.getElementById('contact')
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
        setTimeout(() => {
          this.loading = false
        }, 1000)
      }
    },

    openSocial(link) {
      window.open(link, '_blank')
    }
  }
}
</script>

<style scoped>
.about-section {
  background: linear-gradient(135deg, #1a1a1a, #2d2d2d);
  color: #FFFFFF;
  min-height: 100vh;
  position: relative;
}

.glass-effect {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
}

.profile-card {
  position: relative;
  overflow: hidden;
  transition: all 0.3s ease;
}

.image-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.7);
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: opacity 0.3s ease;
}

.text-header {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  background: linear-gradient(45deg, #FFA500, #FF4500);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  position: relative;
}

.cursor {
  animation: blink 1s infinite;
  color: #FFA500;
}

@keyframes blink {

  0%,
  100% {
    opacity: 1;
  }

  50% {
    opacity: 0;
  }
}

.role-chip {
  transition: transform 0.2s ease;
}

.role-chip:hover {
  transform: translateY(-2px);
}

.skill-card {
  height: 100%;
  transition: all 0.3s ease;
}

.skill-card.on-hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.skill-name {
  font-weight: 500;
  margin-bottom: 8px;
}

.timeline-card {
  transition: all 0.3s ease;
}

.timeline-card.on-hover {
  transform: scale(1.02);
}

.hire-btn {
  background: linear-gradient(45deg, #FFA500, #FF4500);
  color: white;
  font-weight: 600;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  min-width: 250px;
}

.hire-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(255, 165, 0, 0.3);
}

/* Responsive adjustments */
@media (max-width: 600px) {
  .text-header {
    font-size: 2rem;
  }

  .timeline-custom {
    padding: 0;
  }
}
</style>