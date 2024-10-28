<template>
  <section class="contact-us" id="contact">
    <div class="animated-bg"></div>
    <v-container class="py-8 px-4">
      <v-card flat class="contact-card pa-4">
        <v-row justify="center">
          <!-- Developer Scene Column -->
          <v-col cols="12" md="7" lg="8" class="developer-scene-col">
            <div class="section-title mb-6">
              <div class="title-wrapper">
                <h2 class="text-h4 green--text font-weight-bold mb-2">FULL STACK DEVELOPER</h2>
                <div class="animated-underline"></div>
              </div>
            </div>
            
            <!-- Developer Scene -->
            <div class="scene-container">
              <svg viewBox="0 0 800 400" xmlns="http://www.w3.org/2000/svg">
                <!-- Background Elements -->
                <defs>
                  <linearGradient id="grid-gradient" x1="0" y1="0" x2="1" y2="1">
                    <stop offset="0%" stop-color="#2c3e50" />
                    <stop offset="100%" stop-color="#3498db" />
                  </linearGradient>
                </defs>
                
                <!-- Grid Pattern -->
                <pattern id="grid" x="0" y="0" width="40" height="40" patternUnits="userSpaceOnUse">
                  <path d="M 40 0 L 0 0 0 40" fill="none" stroke="rgba(52, 152, 219, 0.1)" stroke-width="1"/>
                </pattern>
                <rect width="100%" height="100%" fill="url(#grid)" class="rotating"/>

                <!-- Frontend Section -->
                <g class="floating">
                  <!-- Browser Window -->
                  <rect x="50" y="50" width="200" height="150" rx="10" fill="#fff" />
                  <rect x="50" y="50" width="200" height="25" rx="10" fill="#e0e0e0" />
                  <circle cx="70" cy="62" r="5" fill="#ff5f57" />
                  <circle cx="90" cy="62" r="5" fill="#febc2e" />
                  <circle cx="110" cy="62" r="5" fill="#28c840" />
                  
                  <!-- Code Elements -->
                  <rect x="65" y="90" width="170" height="10" rx="2" fill="#e0e0e0" />
                  <rect x="65" y="110" width="140" height="10" rx="2" fill="#e0e0e0" />
                  <rect x="65" y="130" width="160" height="10" rx="2" fill="#e0e0e0" />
                  <rect x="65" y="150" width="130" height="10" rx="2" fill="#e0e0e0" />
                </g>

                <!-- Backend Section -->
                <g class="floating-delayed">
                  <!-- Server Stack -->
                  <rect x="550" y="50" width="200" height="150" rx="10" fill="#2c3e50" />
                  <rect x="570" y="70" width="160" height="20" rx="5" fill="#34495e" class="pulse" />
                  <rect x="570" y="100" width="160" height="20" rx="5" fill="#34495e" class="pulse" />
                  <rect x="570" y="130" width="160" height="20" rx="5" fill="#34495e" class="pulse" />
                  
                  <!-- Server Lights -->
                  <circle cx="740" cy="80" r="5" fill="#27ae60" class="glow" />
                  <circle cx="740" cy="110" r="5" fill="#27ae60" class="glow" />
                  <circle cx="740" cy="140" r="5" fill="#27ae60" class="glow" />
                </g>

                <!-- Database Section -->
                <g class="floating">
                  <!-- Database Icon -->
                  <path d="M350 250 C350 230 450 230 450 250 L450 310 C450 330 350 330 350 310 Z" fill="#3498db" />
                  <path d="M350 250 C350 270 450 270 450 250" fill="none" stroke="#fff" stroke-width="2" />
                  <path d="M350 280 C350 300 450 300 450 280" fill="none" stroke="#fff" stroke-width="2" />
                </g>

                <!-- Connection Lines -->
                <g class="fade-move">
                  <path d="M250 125 L350 250" stroke="#3498db" stroke-width="3" stroke-dasharray="10" class="connection-line" />
                  <path d="M450 250 L550 125" stroke="#3498db" stroke-width="3" stroke-dasharray="10" class="connection-line" />
                </g>

                <!-- Data Flow Particles -->
                <g class="pulse">
                  <circle cx="300" cy="187" r="5" fill="#e74c3c" class="glow" />
                  <circle cx="500" cy="187" r="5" fill="#e74c3c" class="glow" />
                </g>

                <!-- Technology Icons -->
                <g class="floating-delayed">
                  <text x="70" y="230" fill="#fff" font-family="Arial" font-size="12">React</text>
                  <text x="150" y="230" fill="#fff" font-family="Arial" font-size="12">Vue</text>
                  <text x="220" y="230" fill="#fff" font-family="Arial" font-size="12">Angular</text>
                </g>
                <g class="floating">
                  <text x="550" y="230" fill="#fff" font-family="Arial" font-size="12">Node.js</text>
                  <text x="620" y="230" fill="#fff" font-family="Arial" font-size="12">Python</text>
                  <text x="690" y="230" fill="#fff" font-family="Arial" font-size="12">Java</text>
                </g>
              </svg>
            </div>
          </v-col>

          <!-- Contact Info Column -->
          <v-col cols="12" md="5" lg="4" class="contact-info-col">
            <div class="section-title mb-6">
              <div class="title-wrapper">
                <h2 class="text-h4 green--text font-weight-bold mb-2">CONTACT ME</h2>
                <div class="animated-underline"></div>
              </div>
            </div>

            <div class="contact-details pa-4 rounded-lg">
              <v-hover v-slot="{ hover }">
                <div class="profile-card mb-6">
                  <v-avatar size="120" class="mb-4">
                    <v-img
                      src="@/assets/img/mypic.png"
                      alt="Profile"
                      :class="{ 'scale-up': hover }"
                    ></v-img>
                  </v-avatar>
                  <h3 class="text-h6 font-weight-bold mb-2">Marry Joy Bersabal</h3>
                  <p class="text-subtitle-1 grey--text">Full Stack Developer</p>
                </div>
              </v-hover>

              <div class="contact-item d-flex align-center mb-4 animate-hover">
                <v-icon color="green" class="mr-2">mdi-phone</v-icon>
                <span>+63 946 654 8239</span>
              </div>

              <div class="social-links d-flex justify-center flex-wrap">
                <v-hover v-for="social in socialLinks" :key="social.name" v-slot="{ hover }">
                  <v-btn
                    :href="social.url"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="social-btn mr-2 mb-2"
                    fab
                    :color="social.color"
                    :elevation="hover ? 8 : 2"
                    :class="{ 'scale-up': hover }"
                  >
                    <v-icon>{{ social.icon }}</v-icon>
                  </v-btn>
                </v-hover>
              </div>

              <v-hover v-slot="{ hover }">
                <v-btn
                  href="https://drive.google.com/file/d/1tyXz0_4FZDDdeg8Y-h2H_vkkTZEyXKb3/view?usp=sharing"
                  color="#FAA300"
                  class="resume-btn white--text mt-6 px-6"
                  :elevation="hover ? 8 : 2"
                  rounded
                  block
                  @click="downloadResume"
                >
                  <v-icon left>mdi-download</v-icon>
                  Download Resume
                </v-btn>
              </v-hover>
            </div>
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data: () => ({
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
  methods: {
    downloadResume() {
      console.log('Downloading resume...');
    }
  }
}
</script>

<style scoped>
.contact-us {
  background-color: #1a1a1a;
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.scene-container {
  background: linear-gradient(45deg, #1a1a1a, #2c3e50);
  padding: 2rem;
  border-radius: 16px;
  position: relative;
  overflow: hidden;
  min-height: 400px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.2);
}

.floating {
  animation: float 3s ease-in-out infinite;
}

.floating-delayed {
  animation: float 3s ease-in-out 1.5s infinite;
}

.rotating {
  animation: rotate 10s linear infinite;
}

.pulse {
  animation: pulse 2s ease-in-out infinite;
}

.fade-move {
  animation: fadeMove 4s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes pulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.1); opacity: 0.8; }
}

@keyframes fadeMove {
  0%, 100% { transform: translateX(0); opacity: 0.8; }
  50% { transform: translateX(20px); opacity: 1; }
}

.glow {
  filter: drop-shadow(0 0 8px rgba(0, 150, 255, 0.6));
}

.connection-line {
  stroke-dasharray: 10;
  animation: dash 1s linear infinite;
}

@keyframes dash {
  to { stroke-dashoffset: -20; }
}

.animated-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, rgba(110, 114, 113, 0.8), rgba(0, 0, 0, 0.3));
  z-index: 0;
}

.contact-card {
  background-color: transparent !important;
  position: relative;
  z-index: 1;
}

.title-wrapper {
  position: relative;
  display: inline-block;
}

.animated-underline {
  position: absolute;
  bottom: -10px;
  left: 0;
  width: 60px;
  height: 3px;
  background-color: #FAA300;
  transform-origin: left;
  animation: expandWidth 0.3s ease-out forwards;
}

@keyframes expandWidth {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}

.contact-details {
  background-color: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.contact-details:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
}

.profile-card {
  text-align: center;
  transition: all 0.3s ease;
}

.scale-up {
  transform: scale(1.05);
}

.social-btn {
  transition: all 0.3s ease;
}

.animate-hover {
  transition: all 0.3s ease;
}

.animate-hover:hover {
  transform: translateX(5px);
}

/* Responsive Styles */
@media (max-width: 960px) {
  .contact-info-col {
    margin-top: 2rem;
  }
  
  .section-title {
    text-align: center;
  }
  
  .animated-underline {
    left: 50%;
    transform: translateX(-50%) scaleX(0);
  }
  
  .animated-underline.active {
    transform: translateX(-50%) scaleX(1);
  }
}

@media (max-width: 600px) {
  .contact-us {
    padding: 2rem 0;
  }

  .section-title .text-h4 {
    font-size: 1.5rem !important;
  }

  .contact-details {
    padding: 1rem !important;
  }
}

/* Dark mode considerations */
@media (prefers-color-scheme: dark) {
  .contact-details {
    background-color: rgba(0, 0, 0, 0.2);
  }
}
</style>