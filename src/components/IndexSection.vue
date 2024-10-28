<template>

  
      <section class="hero-section" id="index">
        <div class="animated-bg"></div>
        <v-container fluid class="pa-0">
          <v-row align="center" justify="center" class="min-vh-100">
            <!-- Left Content Column -->
            <v-col cols="12" md="6" class="content-col">
              <v-slide-y-transition>
                <div class="content-wrapper glass-effect">
                  <!-- Animated Title -->
                  <h1 class="text-header mb-4">
                    <span class="typing-text">{{ displayText }}</span>
                    <span class="cursor">|</span>
                  </h1>
                  
                  <!-- Animated Role Tags -->
                  <div class="role-tags mb-6">
                    <v-slide-x-transition group>
                      <v-chip
                        v-for="(role, index) in roles"
                        :key="role"
                        :color="roleColors[index]"
                        class="ma-2 role-chip"
                        variant="elevated"
                        :style="{ transitionDelay: `${index * 200}ms` }"
                      >
                        <v-icon start class="mr-2">{{ roleIcons[index] }}</v-icon>
                        {{ role }}
                      </v-chip>
                    </v-slide-x-transition>
                  </div>

                  <!-- Bio Text with Typing Effect -->
                  <p class="bio-text" v-html="formattedBioText"></p>

                  <!-- CTA Buttons -->
                  <div class="cta-buttons mt-8">
                    <v-btn
                      href="#contact"
                      size="x-large"
                      elevation="4"
                      class="hire-btn mr-4"
                      @mouseenter="btnHoverEffect"
                    >
                      <v-icon start>mdi-handshake</v-icon>
                      Hire Me
                      <v-icon end class="ml-2">mdi-arrow-right</v-icon>
                    </v-btn>

                  
                  </div>

                  <!-- Social Links -->
                  <div class="social-links mt-12">
                    <v-slide-x-transition group>
                      <v-hover
                        v-for="(social, index) in socialLinks"
                        :key="social.name"
                        v-slot="{ isHovering, props }"
                      >
                        <v-btn
                          v-bind="props"
                          :href="social.url"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="social-btn ma-2"
                          :style="{
                            transitionDelay: `${index * 100}ms`,
                            transform: isHovering ? 'translateY(-5px)' : 'none'
                          }"
                          :color="social.color"
                          icon
                          elevation="4"
                        >
                          <v-icon size="24">{{ social.icon }}</v-icon>
                          
                          <v-tooltip
                            activator="parent"
                            location="top"
                          >
                            {{ social.name }}
                          </v-tooltip>
                        </v-btn>
                      </v-hover>
                    </v-slide-x-transition>
                  </div>
                </div>
              </v-slide-y-transition>
            </v-col>

            <!-- Right Image Column -->
            <v-col cols="12" md="6" class="image-col">
              <v-hover v-slot="{ isHovering, props }">
                <div 
                  class="image-wrapper"
                  v-bind="props"
                  :class="{ 'image-hover': isHovering }"
                >
                  <div>
                    <v-img
                      src="@/assets/img/mypic.png"
                      :aspect-ratio="1"
                      cover
                      class="profile-image"
                      :class="{ 'zoom': isHovering }"
                    >
                      <template v-slot:placeholder>
                        <v-row align="center" justify="center" class="fill-height">
                          <v-progress-circular 
                            indeterminate 
                            color="orange"
                          />
                        </v-row>
                      </template>

                      
                    </v-img>
                  </div>
                </div>
              </v-hover>
            </v-col>
          </v-row>
        </v-container>

      
      </section>
 
</template>

<script>
export default {
  name: "EnhancedHomePage",
  
  data: () => ({
    displayText: '',
    fullText: "Full Stack Developer",
    roles: ['Web Developer', 'App Developer', 'UI/UX Designer'],
    roleColors: ['orange', 'deep-orange', 'amber'],
    roleIcons: ['mdi-web', 'mdi-cellphone', 'mdi-palette'],
    bioText: "Hi, I'm <span class='highlight'>Marry Joy Bersabal</span>. A Bachelor of Science in Information Technology with expertise in web development, app development, and graphic design.",
    socialLinks: [
      {
        name: 'Facebook',
        url: 'https://www.facebook.com/yams.bersabal',
        icon: 'mdi-facebook',
        color: '#1877F2'
      },
      {
        name: 'LinkedIn',
        url: 'https://www.linkedin.com/in/marry-joy-bersabal-2ba726332/',
        icon: 'mdi-linkedin',
        color: '#0A66C2'
      },
      {
        name: 'GitHub',
        url: 'https://github.com/MarryJoyBersabal',
        icon: 'mdi-github',
        color: '#24292F'
      }
    ]
  }),

  computed: {
    formattedBioText() {
      return this.bioText;
    }
  },

  mounted() {
    this.typeText();
    this.initParticles();
  },

  methods: {
    async typeText() {
      let i = 0;
      const typingInterval = setInterval(() => {
        if (i < this.fullText.length) {
          this.displayText = this.fullText.slice(0, i + 1);
          i++;
        } else {
          clearInterval(typingInterval);
          setTimeout(() => {
            this.displayText = ''; 
            i = 0; 
            this.typeText(); 
          }, 2000); 
        }
      }, 100); 
    },

    btnHoverEffect(event) {
      const btn = event.target;
      const ripple = document.createElement('div');
      ripple.classList.add('btn-ripple');
      btn.appendChild(ripple);
      setTimeout(() => ripple.remove(), 1000);
    },

    initParticles() {
     
    }
  }
}
</script>


<style scoped>

html, body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  width: 100%;
}
.container {
  max-width: 100%;

}
.min-vh-100{
  min-height: 100vh;
  width: 100%;
  margin: 0;
  padding: 0;
}
.content-col, .image-col{
  padding: 0;
}

.hero-section {
  background: linear-gradient(135deg, #1a1a1a, #2d2d2d);
  color: #FFFFFF;
  min-height: 100vh;
  position: relative;
  overflow: hidden;
}

.animated-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 20%, rgba(250, 163, 0, 0.1) 0%, transparent 40%),
    radial-gradient(circle at 80% 80%, rgba(250, 163, 0, 0.1) 0%, transparent 40%);
  filter: blur(50px);
  z-index: 0;
}

.glass-effect {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
}

.content-wrapper {
  padding: 3rem;
  position: relative;
  z-index: 1;
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
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.role-chip {
  transition: all 0.3s ease;
}

.role-chip:hover {
  transform: scale(1.1);
}

.bio-text {
  font-size: 1.2rem;
}

.cta-buttons {
  display: flex;
  flex-direction: column;
}

.social-links {
  display: flex;
  justify-content: center;
}

.image-col {
  position: relative;
}

.image-wrapper {
  position: relative;
  overflow: hidden;
}

.image-hover {
  transform: scale(1.05);
  transition: transform 0.3s ease;
}

.image-frame {
  border-radius: 50%;
  overflow: hidden;
  position: relative;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
}

.profile-image {
  border-radius: 50%;
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.image-wrapper:hover .image-overlay {
  opacity: 1;
}

.scroll-indicator {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  text-align: center;
}

.mouse {
  width: 24px;
  height: 40px;
  border: 2px solid white;
  border-radius: 20px;
  position: relative;
}

.wheel {
  width: 8px;
  height: 8px;
  background: white;
  border-radius: 50%;
  position: absolute;
  top: 10px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 1s infinite;
}

@keyframes scroll {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(5px); }
}

.scroll-text {
  color: white;
  margin-top: 10px;
  font-size: 14px;
}
</style>
