<script>
    // Import JSON data from the data folder
    import workExperience from '../data/workExperience.json';
    import hackathons from '../data/hackathons.json';
    import projects from '../data/projects.json';
    import education from '../data/education.json';
    import skillsData from '../data/skills.json';

    import { onMount } from 'svelte';
    let isMobile = false;

    // Function to check window width and update isMobile
    const checkMobile = () => {
        isMobile = window.innerWidth < 768;
    };

    onMount(() => {
        checkMobile();
        window.addEventListener('resize', checkMobile);
        return () => window.removeEventListener('resize', checkMobile);
    });
  </script>
  
  <!-- Wrap the page in a container with dark mode activated -->
  <div class="min-h-screen bg-gray-900 text-gray-100">
    <!-- Header -->
    <header class="bg-gray-800 shadow">
        <div class="container mx-auto px-4 py-4 flex justify-between items-center">
          <div class="text-xl font-bold text-gray-100">Princeton Dychinco</div>
          <!-- Conditionally add horizontal scrolling if on mobile -->
          <nav class={isMobile ? "overflow-x-auto" : ""}>
            <ul class="flex space-x-6 whitespace-nowrap">
              <li><a href="#about" class="text-gray-300 hover:text-gray-100 transition-colors">About</a></li>
              <li><a href="#experience" class="text-gray-300 hover:text-gray-100 transition-colors">Experience</a></li>
              <li><a href="#hackathons" class="text-gray-300 hover:text-gray-100 transition-colors">Hackathons</a></li>
              <li><a href="#projects" class="text-gray-300 hover:text-gray-100 transition-colors">Projects</a></li>
              <li><a href="#skills" class="text-gray-300 hover:text-gray-100 transition-colors">Skills</a></li>
              <li><a href="#education" class="text-gray-300 hover:text-gray-100 transition-colors">Education</a></li>
              <li><a href="#contact" class="text-gray-300 hover:text-gray-100 transition-colors">Contact</a></li>
            </ul>
          </nav>
        </div>
      </header>
  
    <main class="container mx-auto px-4 py-8">
      <!-- Hero Section with a local image and transparent text background -->
      <section id="about" class="relative mb-12 rounded overflow-hidden">
        <!-- svelte-ignore a11y_img_redundant_alt -->
        <img
          src="/hero.webp"
          alt="Hero Image"
          class="w-full h-64 object-cover"
        />
        <div class="absolute inset-0 bg-black opacity-40"></div>
        <div class="relative p-6 bg-transparent">
          <h1 class="text-4xl font-bold text-white drop-shadow">Princeton Dychinco</h1>
          <p class="mt-2 text-lg text-gray-200 drop-shadow">
            Software Developer and Data Engineer with expertise in big data, automation, and agile teamwork.
            Passionate about innovative solutions and continuous learning.
          </p>
        </div>
      </section>
  
      <!-- Work Experience Section -->
      <section id="experience" class="mb-12">
        <h2 class="text-3xl font-semibold text-gray-100 border-b pb-2 mb-6">Work Experience</h2>
        <div class="space-y-6">
          {#each workExperience as job}
            <div class="p-6 bg-gray-800 rounded-lg shadow hover:shadow-lg transition-shadow">
              <p class="font-bold text-xl text-gray-100">{job.title} • {job.company}</p>
              <p class="text-sm text-gray-400 italic">{job.location} | {job.period}</p>
              <p class="mt-3 text-gray-300">{job.details}</p>
            </div>
          {/each}
        </div>
      </section>
  
      <!-- Hackathons Section -->
      <section id="hackathons" class="mb-12">
        <h2 class="text-3xl font-semibold text-gray-100 border-b pb-2 mb-6">Hackathons</h2>
        <div class="space-y-6">
          {#each hackathons as hack}
            <div class="p-6 bg-gray-800 rounded-lg shadow hover:shadow-lg transition-shadow">
              <p class="font-bold text-xl text-gray-100">{hack.name}</p>
              <p class="mt-3 text-gray-300">{hack.details}</p>
            </div>
          {/each}
        </div>
      </section>
  
      <!-- Projects Section -->
      <section id="projects" class="mb-12">
        <h2 class="text-3xl font-semibold text-gray-100 border-b pb-2 mb-6">Projects</h2>
        <div class="space-y-6">
          {#each projects as project}
            <div class="p-6 bg-gray-800 rounded-lg shadow hover:shadow-lg transition-shadow">
              <p class="font-bold text-xl text-gray-100">{project.name}</p>
              <p class="mt-3 text-gray-300">{project.details}</p>
            </div>
          {/each}
        </div>
      </section>
  
      <!-- Skills Section -->
      <section id="skills" class="mb-12">
        <h2 class="text-3xl font-semibold text-gray-100 border-b pb-2 mb-6">Languages &amp; Frameworks</h2>
        <div class="p-6 bg-gray-800 rounded-lg shadow hover:shadow-lg transition-shadow">
          <p class="text-gray-300 text-lg">{skillsData.list}</p>
        </div>
      </section>
  
      <!-- Education Section -->
      <section id="education" class="mb-12">
        <h2 class="text-3xl font-semibold text-gray-100 border-b pb-2 mb-6">Education</h2>
        <div class="space-y-6">
          {#each education as school}
            <div class="p-6 bg-gray-800 rounded-lg shadow hover:shadow-lg transition-shadow">
              <p class="font-bold text-xl text-gray-100">{school.institution} – {school.program}</p>
              <p class="text-sm text-gray-400 italic">{school.location} | {school.period}</p>
            </div>
          {/each}
        </div>
      </section>
  
      <!-- Contact Section -->
      <section id="contact" class="mb-12">
        <h2 class="text-3xl font-semibold text-gray-100 border-b pb-2 mb-6">Contact</h2>
        <div class="p-6 bg-gray-800 rounded-lg shadow hover:shadow-lg transition-shadow">
          <p class="text-gray-300 text-lg">
            <a href="https://linkedin.com/in/prdychinco" target="_blank" class="text-blue-400 hover:text-blue-300 transition-colors">LinkedIn</a> •
            <a href="https://github.com/pdychinco" target="_blank" class="text-blue-400 hover:text-blue-300 transition-colors">GitHub</a>
          </p>
        </div>
      </section>
    </main>
  
    <!-- Footer -->
    <footer class="bg-gray-800 shadow py-4">
      <div class="container mx-auto text-center text-gray-400">
        &copy; {new Date().getFullYear()} Princeton Dychinco. All rights reserved.
      </div>
    </footer>
  </div>
  