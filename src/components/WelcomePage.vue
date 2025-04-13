<template>
    <div class="portfolio" :class="{ 'dark': isDarkMode }">
      <div class="dark:bg-gray-900 dark:text-white transition-colors duration-300">
        <!-- Navigation -->
        <nav class="fixed top-0 left-0 right-0 bg-white dark:bg-gray-800 shadow-md z-50 transition-colors duration-300">
          <div class="container mx-auto px-6 py-3">
            <div class="flex justify-between items-center">
              <a href="#" class="text-xl font-bold dark:text-white">Portfolio</a>
              <div class="hidden md:flex space-x-8 items-center">
                <a v-for="item in navItems" :key="item.id" 
                  :href="`#${item.id}`" 
                  class="text-gray-700 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white transition-colors">
                  {{ item.name }}
                </a>
                <button 
                  @click="toggleDarkMode" 
                  class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors"
                  aria-label="Toggle dark mode"
                >
                  <SunIcon v-if="isDarkMode" class="h-5 w-5 text-yellow-400" />
                  <MoonIcon v-else class="h-5 w-5 text-gray-700" />
                </button>
              </div>
              <div class="flex items-center md:hidden">
                <button 
                  @click="toggleDarkMode" 
                  class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors mr-2"
                  aria-label="Toggle dark mode"
                >
                  <SunIcon v-if="isDarkMode" class="h-5 w-5 text-yellow-400" />
                  <MoonIcon v-else class="h-5 w-5 text-gray-700" />
                </button>
                <button @click="mobileMenuOpen = !mobileMenuOpen">
                  <MenuIcon v-if="!mobileMenuOpen" class="h-6 w-6 dark:text-white" />
                  <XIcon v-else class="h-6 w-6 dark:text-white" />
                </button>
              </div>
            </div>
          </div>
          <!-- Mobile menu -->
          <div v-if="mobileMenuOpen" class="md:hidden bg-white dark:bg-gray-800 shadow-md transition-colors duration-300">
            <div class="container mx-auto px-6 py-3">
              <div class="flex flex-col space-y-4">
                <a v-for="item in navItems" :key="item.id" 
                  :href="`#${item.id}`" 
                  @click="mobileMenuOpen = false"
                  class="text-gray-700 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white transition-colors">
                  {{ item.name }}
                </a>
              </div>
            </div>
          </div>
        </nav>
  
        <!-- Hero Section -->
        <section id="home" class="min-h-screen flex items-center pt-16 dark:bg-gray-900 transition-colors duration-300">
          <div class="container mx-auto px-6">
            <div class="flex flex-col md:flex-row items-center">
              <div class="md:w-1/2 text-center md:text-left">
                <h1 class="text-4xl md:text-5xl font-bold mb-4 dark:text-white">Hi, I'm <span class="text-emerald-600 dark:text-emerald-400">Vladimir</span></h1>
                <h2 class="text-2xl md:text-3xl text-gray-600 dark:text-gray-300 mb-6">Backend Developer</h2>
                <p class="text-gray-600 dark:text-gray-400 mb-8 max-w-lg">
                  I make the behind-the-scenes magic happen so apps don’t break.
                </p>
                <div class="flex space-x-4 justify-center md:justify-start">
                  <a href="#contact" class="bg-emerald-600 hover:bg-emerald-700 text-white px-6 py-3 rounded-md transition-colors">
                    Contact Me
                  </a>
                  <a href="#projects" class="border border-emerald-600 text-emerald-600 hover:bg-emerald-50 dark:text-emerald-400 dark:border-emerald-400 dark:hover:bg-emerald-900/30 px-6 py-3 rounded-md transition-colors">
                    View Work
                  </a>
                </div>
              </div>
              <div class="md:w-1/2 mt-12 md:mt-0">
                <div class="w-100 h-100 mx-auto bg-gray-200 dark:bg-gray-700 rounded-full overflow-hidden">
                  <img :src="profileImage" alt="Profile" class="w-full h-full object-cover" />
                </div>
              </div>
            </div>
          </div>
        </section>
  
        <!-- About Section -->
        <section id="about" class="py-20 bg-gray-50 dark:bg-gray-800 transition-colors duration-300">
          <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-12 dark:text-white">About Me</h2>
            <div class="flex flex-col md:flex-row items-center">
              <div class="md:w-1/2 mb-8 md:mb-0">
                <img :src="profileImage2" alt="About me" class="rounded-lg shadow-lg max-w-full h-auto" />
              </div>
              <div class="md:w-1/2 md:pl-12">
                <p class="text-gray-600 dark:text-gray-300 mb-6">
                  Hey, I’m Vlad — a backend developer who loves building fast, reliable, and scalable systems. I'm currently a 3rd-year BSc-IT student, diving deep into APIs, databases, and all things server-side. I focus on writing clean code that keeps things running smoothly behind the scenes, so frontends can shine without breaking a sweat.
                </p>
                <p class="text-gray-600 dark:text-gray-300 mb-6">
                  I specialize in building backend systems that are efficient, scalable, and built to last. With a focus on performance and reliability, I ensure that the systems I develop not only meet the needs of today but can also handle tomorrow's challenges. I aim to create clean, maintainable code that ensures seamless performance, allowing the front-end to shine without any server-side hiccups.                </p>
                <div class="flex flex-wrap gap-2">
                    <span v-for="tag in ['Vue.js', 'MySQL', '.NET (C#)','Backend Development']" :key="tag" class="bg-emerald-100 text-emerald-800 dark:bg-emerald-900/50 dark:text-emerald-300 px-3 py-1 rounded-full text-sm">
                    {{ tag }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </section>
  
        <!-- Skills Section -->
        <section id="skills" class="py-20 dark:bg-gray-900 transition-colors duration-300">
          <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-12 dark:text-white">My Skills</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
              <div v-for="skill in skills" :key="skill.name" class="bg-white dark:bg-gray-800 p-6 rounded-lg shadow-md">
                <div class="flex items-center mb-4">
                  <component :is="skill.icon" class="h-6 w-6 text-emerald-600 dark:text-emerald-400 mr-2" />
                  <h3 class="text-xl font-semibold dark:text-white">{{ skill.name }}</h3>
                </div>
                <div class="w-full bg-gray-200 dark:bg-gray-700 rounded-full h-2.5 mb-2">
                  <div class="bg-emerald-600 dark:bg-emerald-500 h-2.5 rounded-full" :style="{ width: `${skill.level}%` }"></div>
                </div>
                <p class="text-gray-600 dark:text-gray-300">{{ skill.description }}</p>
              </div>
            </div>
          </div>
        </section>
  
        <!-- Projects Section -->
        <section id="projects" class="py-20 bg-gray-50 dark:bg-gray-800 transition-colors duration-300">
          <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-4 dark:text-white">My Projects</h2>
            <p class="text-gray-600 dark:text-gray-300 text-center mb-12 max-w-2xl mx-auto">
              Here are some of my recent projects. Each one was carefully crafted to solve specific problems and deliver exceptional user experiences.
            </p>
            
            <div class="mb-8 flex justify-center">
              <div class="flex flex-wrap gap-2">
                <button 
                  v-for="category in ['All', 'Web', 'Mobile', 'Design']" 
                  :key="category"
                  @click="activeCategory = category"
                  :class="[
                    'px-4 py-2 rounded-md transition-colors',
                    activeCategory === category 
                      ? 'bg-emerald-600 dark:bg-emerald-500 text-white' 
                      : 'bg-white dark:bg-gray-700 text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-600'
                  ]"
                >
                  {{ category }}
                </button>
              </div>
            </div>
            
            <div v-if="filteredProjects.length > 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
              <div 
                v-for="project in filteredProjects" 
                :key="project.id" 
                class="bg-white dark:bg-gray-800 rounded-lg overflow-hidden shadow-md transition-transform hover:scale-105"
              >
                <img :src="project.image" :alt="project.title" class="w-full h-48 object-cover" />
                <div class="p-6">
                  <h3 class="text-xl font-bold mb-2 dark:text-white">{{ project.title }}</h3>
                  <p class="text-gray-600 dark:text-gray-300 mb-4">{{ project.description }}</p>
                  <div class="flex flex-wrap gap-2 mb-4">
                    <span 
                      v-for="tag in project.tags" 
                      :key="tag" 
                      class="bg-gray-100 dark:bg-gray-700 text-gray-800 dark:text-gray-300 px-2 py-1 rounded-full text-xs"
                    >
                      {{ tag }}
                    </span>
                  </div>
                  <div class="flex space-x-3">
                    <a :href="project.demo" class="text-emerald-600 dark:text-emerald-400 hover:text-emerald-700 dark:hover:text-emerald-300 flex items-center">
                      <ExternalLinkIcon class="h-4 w-4 mr-1" />
                      Demo
                    </a>
                    <a :href="project.github" class="text-emerald-600 dark:text-emerald-400 hover:text-emerald-700 dark:hover:text-emerald-300 flex items-center">
                      <GithubIcon class="h-4 w-4 mr-1" />
                      Code
                    </a>
                  </div>
                </div>
              </div>
            </div>
  
            <div v-else class="bg-white dark:bg-gray-800 rounded-lg shadow-md p-12 text-center max-w-2xl mx-auto">
              <FolderIcon class="h-16 w-16 mx-auto text-gray-300 dark:text-gray-600 mb-4" />
              <h3 class="text-xl font-bold mb-2 dark:text-white">No Projects Yet</h3>
              <p class="text-gray-600 dark:text-gray-300 mb-6">
                I'm currently working on some exciting projects that will be showcased here soon.
              </p>
              <p class="text-gray-500 dark:text-gray-400 text-sm">
                Check back later or contact me to learn about what I'm currently working on.
              </p>
            </div>
          </div>
        </section>
  
        <!-- Contact Section -->
        <section id="contact" class="py-20 dark:bg-gray-900 transition-colors duration-300">
          <div class="container mx-auto px-6">
            <h2 class="text-3xl font-bold text-center mb-12 dark:text-white">Get In Touch</h2>
            <div class="max-w-3xl mx-auto">
              <div class="bg-white dark:bg-gray-800 rounded-lg shadow-lg p-8">
                <form @submit.prevent="submitForm" class="space-y-6">
                  <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div>
                      <label for="name" class="block text-gray-700 dark:text-gray-300 mb-2">Name</label>
                      <input 
                        type="text" 
                        id="name" 
                        v-model="contactForm.name" 
                        placeholder="John Doe"
                        class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                        required
                      />
                    </div>
                    <div>
                      <label for="email" class="block text-gray-700 dark:text-gray-300 mb-2">Email</label>
                      <input 
                        type="email" 
                        id="email" 
                        placeholder="johndoe@example.com"
                        v-model="contactForm.email" 
                        class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                        required
                      />
                    </div>
                  </div>
                  <div>
                    <label for="subject" class="block text-gray-700 dark:text-gray-300 mb-2">Subject</label>
                    <input 
                      type="text" 
                      id="subject"
                      placeholder="Subject"
                      v-model="contactForm.subject" 
                      class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                      required
                    />
                  </div>
                  <div>
                    <label for="message" class="block text-gray-700 dark:text-gray-300 mb-2">Message</label>
                    <textarea 
                      id="message" 
                      v-model="contactForm.message" 
                      rows="5"
                      placeholder="Your message here..." 
                      class="w-full px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-emerald-500 dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                      required
                    ></textarea>
                  </div>
                  <button 
                    type="submit" 
                    class="bg-emerald-600 hover:bg-emerald-700 dark:bg-emerald-500 dark:hover:bg-emerald-600 text-white px-6 py-3 rounded-md transition-colors w-full"
                    :disabled="formSubmitting"
                  >
                    <span v-if="formSubmitting">Sending...</span>
                    <span v-else>Send Message</span>
                  </button>
                  <p v-if="formSuccess" class="text-emerald-600 dark:text-emerald-400 text-center">
                    Your message has been sent successfully!
                  </p>
                </form>
              </div>
            </div>
          </div>
        </section>
  
        <!-- Footer -->
        <footer class="bg-gray-800 dark:bg-gray-900 text-white py-12 transition-colors duration-300">
          <div class="container mx-auto px-6">
            <div class="flex flex-col md:flex-row justify-between items-center">
              <div class="mb-6 md:mb-0">
                <h3 class="text-xl font-bold">Portfolio</h3>
                <p class="text-gray-400 mt-2">Copyright © 2025 Vladimir Clint Catigan. All rights reserved.</p>
              </div>
              <div class="flex space-x-6">
                <a href="https://github.com/notaprogrammervlad/" class="text-gray-400 hover:text-white transition-colors">
                  <GithubIcon class="h-6 w-6" />
                </a>
                <a href="https://www.linkedin.com/in/vcgcatigan/" class="text-gray-400 hover:text-white transition-colors">
                  <LinkedinIcon class="h-6 w-6" />
                </a>
                <a href="https://www.instagram.com/dmir.klnt/" class="text-gray-400 hover:text-white transition-colors">
                  <InstagramIcon class="h-6 w-6" />
                </a>
              </div>
            </div>
          </div>
        </footer>
      </div>
    </div>
  </template>
  
  <script setup>
  import profileImage from '../assets/profile-pic-99999.png'
  import profileImage2 from '../assets/profile-pic-99998.jpg'
  import { ref, computed, onMounted, watch } from 'vue'
  import { 
    Menu as MenuIcon, 
    X as XIcon, 
    ExternalLink as ExternalLinkIcon,
    Github as GithubIcon,
    Linkedin as LinkedinIcon,
    Twitter as TwitterIcon,
    Instagram as InstagramIcon,
    Code as CodeIcon,
    Layout as LayoutIcon,
    Smartphone as SmartphoneIcon,
    Database as DatabaseIcon,
    Server as ServerIcon,
    Figma as FigmaIcon,
    Folder as FolderIcon,
    Moon as MoonIcon,
    Sun as SunIcon
  } from 'lucide-vue-next'

  
  // Dark mode
  const isDarkMode = ref(false)
  
  // Initialize dark mode from localStorage or system preference
  onMounted(() => {
  // Check localStorage first
    const savedMode = localStorage.getItem('darkMode')
    
    if (savedMode !== null) {
      isDarkMode.value = savedMode === 'true'
    } else {
      // If no saved preference, check system preference
      isDarkMode.value = window.matchMedia('(prefers-color-scheme: dark)').matches
    }
  })
  
  // Toggle dark mode
  const toggleDarkMode = () => {
    isDarkMode.value = !isDarkMode.value
    localStorage.setItem('darkMode', isDarkMode.value.toString())
  }
  
  // Watch for system preference changes
  onMounted(() => {
    const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)')
    
    const handleChange = (e) => {
      // Only update if user hasn't set a preference
      if (localStorage.getItem('darkMode') === null) {
        isDarkMode.value = e.matches
      }
    }
    
    // Modern browsers
    if (mediaQuery.addEventListener) {
      mediaQuery.addEventListener('change', handleChange)
    }
  })
  
  // Navigation
  const navItems = [
    { id: 'home', name: 'Home' },
    { id: 'about', name: 'About' },
    { id: 'skills', name: 'Skills' },
    { id: 'projects', name: 'Projects' },
    { id: 'contact', name: 'Contact' }
  ]
  
  const mobileMenuOpen = ref(false)
  
    // Skills
    const skills = [
    { 
        name: 'Vue.js', 
        level: 80, 
        icon: CodeIcon,
        description: 'Building dynamic and performant web applications using Vue 3, Pinia, and Composition API.'
    },
    { 
        name: 'MySQL', 
        level: 75, 
        icon: DatabaseIcon,
        description: 'Designing and optimizing relational databases, writing efficient queries, and managing data integrity.'
    },
    { 
        name: '.NET (C#)', 
        level: 70, 
        icon: CodeIcon,
        description: 'Developing backend services and APIs using .NET Core, Entity Framework, and MVC architecture.'
    },
    { 
        name: 'Tailwind CSS', 
        level: 60, 
        icon: LayoutIcon,
        description: 'Creating responsive and modern UI components using utility-first CSS with Tailwind.'
    },
    { 
        name: 'Node.js', 
        level: 65, 
        icon: ServerIcon,
        description: 'Building scalable server-side applications and RESTful APIs with Express.js and MySQL.'
    },
    {
        name: 'PHP',
        level: 60,
        icon: DatabaseIcon,
        description: 'Developing dynamic web applications using PHP, Laravel, and MySQL.'
    },
    {
        name: 'Python',
        level: 50,
        icon: CodeIcon,
        description: 'Automating tasks, building web applications, and analyzing data using Python and Django.'
    }
    ];
  
  // Projects
  const projects = []
  
  // Project filtering
  const activeCategory = ref('All')
  const filteredProjects = computed(() => {
    if (activeCategory.value === 'All') {
      return projects
    }
    return projects.filter(project => project.category === activeCategory.value)
  })
  
  // Contact form
  const contactForm = ref({
    name: '',
    email: '',
    subject: '',
    message: ''
  })
  const formSubmitting = ref(false)
  const formSuccess = ref(false)
  
  const submitForm = () => {
    formSubmitting.value = true
    
    // Simulate form submission
    setTimeout(() => {
      formSubmitting.value = false
      formSuccess.value = true
      
      // Reset form
      contactForm.value = {
        name: '',
        email: '',
        subject: '',
        message: ''
      }
      
      // Reset success message after 3 seconds
      setTimeout(() => {
        formSuccess.value = false
      }, 3000)
    }, 1500)
  }
  </script>
  
  <style scoped>
  .portfolio {
    scroll-behavior: smooth;
  }
  
  section {
    scroll-margin-top: 80px;
  }
  
  /* Apply dark mode to the entire document when .dark class is present */
  :global(.dark) {
    color-scheme: dark;
  }

  </style>