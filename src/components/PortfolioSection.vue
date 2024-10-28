<template>
  <v-container id="portfolio" fluid class="portfolio-container py-16">
    <!-- Projects Section -->
    <div class="section-wrapper">
      <div class="section-header fade-in">
        <h1 class="text-header mb-2">Works & Projects</h1>
        <div class="header-line"></div>
        <p class="bio-text mt-4">Showcasing some of my recent work and creative endeavors</p>
      </div>
      
      <v-row class="mt-8">
        <v-col v-for="(project, index) in projects" 
               :key="project.title" 
               cols="12" 
               sm="6" 
               md="4"
               class="project-col"
               :class="{'fade-in-left': index % 3 === 0, 'fade-in-up': index % 3 === 1, 'fade-in-right': index % 3 === 2}">
          <v-card class="project-card glass-effect">
            <div class="project-image-wrapper">
              <v-img :src="project.image" 
                     height="250px" 
                     cover 
                     class="project-image">
                <template v-slot:placeholder>
                  <div class="loading-overlay">
                    <v-progress-circular indeterminate color="#FAA300"></v-progress-circular>
                  </div>
                </template>
              </v-img>
              <div class="project-overlay">
                
              </div>
            </div>
            <v-card-title class="project-title">{{ project.title }}</v-card-title>
            <v-card-text class="project-description">{{ project.description }}</v-card-text>
            <v-card-text class="project-tags">
              <v-chip v-for="tag in project.tags" 
                      :key="tag"
                      class="ma-1 project-tag"
                      size="small">
                {{ tag }}
              </v-chip>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </div>

    <!-- Certificates Section -->
    <div class="section-wrapper mt-16">
      <div class="section-header fade-in">
        <h1 class="text-header mb-2">Certificates</h1>
        <div class="header-line"></div>
        <p class="bio-text mt-4">Professional certifications and achievements</p>
      </div>

      <v-row class="mt-8">
        <v-col v-for="(certificate, index) in certificates" 
               :key="certificate.title" 
               cols="12" 
               sm="6" 
               md="4"
               class="certificate-col"
               :class="{'fade-in-left': index % 3 === 0, 'fade-in-up': index % 3 === 1, 'fade-in-right': index % 3 === 2}">
          <v-card class="certificate-card glass-effect">
            <div class="certificate-image-wrapper">
              <v-img :src="certificate.image" 
                     height="200px" 
                     cover 
                     class="certificate-image"
                     @click="openModal(certificate)">
                <template v-slot:placeholder>
                  <div class="loading-overlay">
                    <v-progress-circular indeterminate color="#FAA300"></v-progress-circular>
                  </div>
                </template>
                <div class="certificate-badge">
                  <v-icon icon="mdi-certificate" color="#FAA300"></v-icon>
                </div>
              </v-img>
            </div>
            <v-card-title class="certificate-title">{{ certificate.title }}</v-card-title>
            <v-card-text class="certificate-description">{{ certificate.description }}</v-card-text>
            <v-card-actions class="certificate-actions">
              <v-btn @click="openModal(certificate)" 
                     class="view-certificate-btn" 
                     rounded="pill"
                     variant="elevated">
                View Certificate
                <v-icon end icon="mdi-eye" class="ml-2"></v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </div>

    <!-- Enhanced Certificate Modal -->
    <v-dialog v-model="dialog" 
              max-width="800px" 
              class="certificate-modal" 
              transition="dialog-bottom-transition">
      <v-card class="modal-card glass-effect">
        <v-card-title class="modal-header">
          <span class="text-header-sub">{{ selectedCertificate?.title }}</span>
          <v-btn icon @click="dialog = false" class="close-btn">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-card-title>
        <v-card-text class="modal-content">
          <v-img :src="selectedCertificate?.image" 
                 class="certificate-modal-image" 
                 contain
                 max-height="500">
          </v-img>
          <div class="certificate-details mt-4">
            <p class="bio-text">{{ selectedCertificate?.description }}</p>
          </div>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  name: 'PortfolioSection',
  data: () => ({
    dialog: false,
    selectedCertificate: null,
    projects: [
      {
        title: 'Chic Nails',
        description: 'Chic Nails is an ultimate mobile appointment app for booking nail services. Users can explore services and book appointments seamlessly.',
        image: require('@/assets/img/chicnails/chicnailsapp.png'),
        link: '#',
        tags: ['Bootsrtap', 'CSS', 'Mobile App']
      },
      {
        title: 'Portfolio Website',
        description: 'A showcase of my work as a Full Stack Developer and Graphic Designer, featuring modern web technologies and responsive design.',
        image: require('@/assets/img/portfolio.png'),
        link: 'https://example.com/my-portfolio',
        tags: ['Vue.js', 'Vuetify', ]
      },
      {
        title: 'Ceissues Forum',
        description: 'A dedicated community forum for Caraga State University students to connect, share insights, and engage in meaningful discussions.',
        image: require('@/assets/img/website.png'),
        link: 'https://example.com/ecommerce-project',
        tags: ['HTML', 'Php', 'CSS','Bootstrap']
      },
    ],
    certificates: [
      {
        title: 'CSS Course Certificate',
        description: 'Advanced CSS and modern design principles certification, focusing on responsive design and animations.',
        image: require('@/assets/img/certificates/CSS.jpg'),
        date: '2023'
      },
      {
        title: 'HTML Course Certificate',
        description: 'Comprehensive HTML5 certification covering semantic markup and modern web standards.',
        image: require('@/assets/img/certificates/html.jpg'),
        date: '2023'
      },
      {
        title: 'JAVA Course Certificate',
        description: 'Advanced Java programming certification with focus on enterprise application development.',
        image: require('@/assets/img/certificates/java.jpg'),
        date: '2023'
      },
      {
        title: 'JavaScript Course Certificate',
        description: 'Modern JavaScript certification covering ES6+ features and async programming.',
        image: require('@/assets/img/certificates/javascript.jpg'),
        date: '2023'
      },
      {
        title: 'Mobile Application Development',
        description: 'Recognition for exceptional performance in mobile application development project.',
        image: require('@/assets/img/certificates/app.jpeg'),
        date: '2023'
      },
      {
        title: 'Graphics Designer Certificate',
        description: 'Professional certification in graphic design, covering modern design principles and tools.',
        image: require('@/assets/img/certificates/graphics.png'),
        date: '2023'
      },
    ]
  }),
  methods: {
    openModal(certificate) {
      this.selectedCertificate = certificate;
      this.dialog = true;
    },
    viewProject(project) {
      window.open(project.link, '_blank');
    }
  }
}
</script>

<style scoped>
.portfolio-container {
  background-color: #1a1a1a;
  color: #FFFFFF;
  min-height: 100vh;
}

.section-wrapper {
  padding: 2rem;
}

.section-header {
  text-align: center;
  margin-bottom: 3rem;
}

.text-header {
  font-size: clamp(2rem, 5vw, 3.5rem);
  line-height: 1.2;
  font-weight: 700;
  color: #FFA500;
  transition: font-size 0.3s ease;
}

.header-line {
  width: 100px;
  height: 4px;
  background: linear-gradient(90deg, transparent, #FAA300, transparent);
  margin: 1rem auto;
}

.bio-text {
  font-family: 'Times New Roman', Times, serif;
  font-size: clamp(1rem, 2vw, 1.25rem);
  line-height: 1.6;
  color: #FFFFFF;
  opacity: 0.9;
}

.glass-effect {
  background-color: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  overflow: hidden;
}

/* Project Card Styles */
.project-card {
  height: 100%;
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.project-card:hover {
  transform: translateY(-10px);
}

.project-image-wrapper {
  position: relative;
  overflow: hidden;
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-image-wrapper:hover .project-overlay {
  opacity: 1;
}

.project-title {
  color: #FAA300;
  font-size: 1.5rem;
  font-weight: 600;
  padding: 1.5rem 1rem 0.5rem;
}

.project-description {
  color: #FFFFFF;
  opacity: 0.9;
  line-height: 1.6;
}

.project-tag {
  background-color: rgba(250, 163, 0, 0.1) !important;
  color: #FFFFFF !important;
  border: 1px solid rgba(250, 163, 0, 0.3);
}

/* Certificate Card Styles */
.certificate-card {
  height: 100%;
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.certificate-card:hover {
  transform: translateY(-10px);
}

.certificate-image-wrapper {
  position: relative;
  cursor: pointer;
}

.certificate-badge {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.5);
  padding: 0.5rem;
  border-radius: 50%;
}

.certificate-title {
  color: #FFA500;
  font-size: 1.25rem;
  font-weight: 600;
  padding: 1.5rem 1rem 0.5rem;
}

.certificate-description {
  color: #FFFFFF;
  opacity: 0.9;
  line-height: 1.6;
}

/* Button Styles */
.view-project-btn,
.view-certificate-btn {
  background-color: #FFA500;
  color: #FFFFFF;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.view-project-btn:hover,
.view-certificate-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(250, 163, 0, 0.3);
}

/* Modal Styles */
.modal-card {
  background-color: rgba(110, 114, 113, 0.95);
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem;
}

.close-btn {
  color: #FFA500;
}

.certificate-modal-image {
  border-radius: 8px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}

/* Loading Overlay */
.loading-overlay {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: rgba(110, 114, 113, 0.5);
}

/* Animations */
.fade-in {
  opacity: 0;
  transform: translateY(30px);
  animation: fadeIn 0.6s forwards;
}

.fade-in-up {
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.6s forwards;
}

.fade-in-right {
  opacity: 0;
  transform: translateX(-30px);
  animation: fadeInRight 0.6s forwards;
}

.fade-in-left {
  opacity: 0;
  transform: translateX(30px);
  animation: fadeInLeft 0.6s forwards;
}

@keyframes fadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInRight {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeInLeft {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>