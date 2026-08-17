<template>
    <section id="projects" class="relative w-full py-24 px-5 sm:px-8 md:px-12 lg:px-8">
        <!-- Background glow -->
        <div class="absolute inset-0 -z-10 overflow-hidden">
            <div class="absolute top-1/3 left-1/4 w-100 h-100 rounded-full bg-pink-500/10 blur-[120px]"></div>
            <div class="absolute bottom-1/4 right-1/4 w-100 h-100 rounded-full bg-cyan-500/10 blur-[120px]">
            </div>
        </div>

        <div class="max-w-5xl lg:max-w-7xl mx-auto">

            <!-- Titre de section -->
            <div class="text-center mb-12">
                <p class="text-cyan-400 text-sm font-semibold uppercase tracking-widest mb-3">
                    Portfolio
                </p>
                <h2 class="text-white font-bold text-3xl md:text-4xl lg:text-5xl">
                    My
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400">
                        Projects
                    </span>
                </h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto text-lg">
                    A selection of recent work — from full-stack platforms to client websites.
                </p>
            </div>

            <!-- Filtres -->
            <div class="flex flex-wrap justify-center gap-3 mb-12">
                <button v-for="cat in categories" :key="cat" @click="activeFilter = cat"
                    class="px-5 py-2 rounded-full text-sm font-medium border transition-all duration-300" :class="activeFilter === cat
                        ? 'bg-linear-to-r from-pink-400 to-cyan-400 text-[#0a0a0f] border-transparent shadow-[0_0_20px_-5px_rgba(34,211,238,0.5)]'
                        : 'text-gray-300 border-white/15 bg-white/3 hover:border-white/30 hover:text-white'">
                    {{ cat }}
                </button>
            </div>

            <!-- Grille de projets -->
            <transition-group tag="div" name="fade" class="grid sm:grid-cols-2 lg:grid-cols-3 gap-8">
                <article v-for="project in filteredProjects" :key="project.title"
                    class="group relative rounded-2xl overflow-hidden bg-white/5 border border-white/10 backdrop-blur-sm hover:border-cyan-400/40 transition-all duration-300 hover:-translate-y-2 hover:shadow-[0_20px_40px_-15px_rgba(0,0,0,0.5)]">

                    <!-- Image -->
                    <div class="relative h-52 overflow-hidden">
                        <img :src="project.image" :alt="project.title" loading="lazy"
                            class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500" />
                        <div class="absolute inset-0 bg-linear-to-t from-[#0a0a0f] via-[#0a0a0f]/30 to-transparent">
                        </div>
                        <!-- Category badge on image -->
                        <span
                            class="absolute top-4 left-4 px-3 py-1 rounded-full text-xs font-semibold text-white bg-black/40 backdrop-blur-md border border-white/15">
                            {{ project.category }}
                        </span>
                    </div>

                    <!-- Contenu -->
                    <div class="p-6">
                        <h3 class="text-white font-semibold text-xl mb-3 group-hover:text-cyan-300 transition-colors">
                            {{ project.title }}
                        </h3>
                        <p class="text-gray-300 text-sm leading-relaxed mb-4">
                            {{ project.description }}
                        </p>

                        <!-- Tags techno -->
                        <div class="flex flex-wrap gap-2 mb-5">
                            <span v-for="tech in project.stack" :key="tech"
                                class="text-xs px-2.5 py-1 rounded-md bg-white/6 border border-white/10 text-gray-300">
                                {{ tech }}
                            </span>
                        </div>

                        <!-- Liens -->
                        <div class="flex gap-4 pt-1 border-t border-white/5">
                            <a v-if="project.demo" :href="project.demo" target="_blank" rel="noopener"
                                class="inline-flex items-center gap-1.5 text-sm font-medium text-white hover:text-pink-400 transition pt-4">
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                                    stroke-width="2">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1" />
                                </svg>
                                Live Demo
                            </a>
                            <a v-if="project.code" :href="project.code" target="_blank" rel="noopener"
                                class="inline-flex items-center gap-1.5 text-sm font-medium text-white hover:text-cyan-400 transition pt-4">
                                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                                    <path
                                        d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z" />
                                </svg>
                                Source Code
                            </a>
                            <span v-if="!project.demo && !project.code" class="text-sm text-gray-500 italic pt-4">
                                Private / NDA project
                            </span>
                        </div>
                    </div>
                </article>
            </transition-group>

            <p v-if="filteredProjects.length === 0" class="text-center text-gray-400 mt-12">
                No projects in this category yet.
            </p>

        </div>
    </section>
</template>

<script>
export default {
    name: 'Projects',
    data() {
        return {
            activeFilter: 'All',
            categories: ['All', 'Web App', 'Mobile', 'WordPress'],
            projects: [
                {
                    title: 'E-Commerce Platform',
                    category: 'Web App',
                    description: 'Contributed to a Laravel/Vue.js e-commerce platform — built backend features and REST APIs, fixed bugs, and integrated payment and external APIs (Edahabia, Flexy, etc.).',
                    image: 'https://images.pexels.com/photos/34577/pexels-photo.jpg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel', 'Vue.js', 'MySQL', 'REST API', 'Payment'],
                    demo: null,
                    code: null
                },
                {
                    title: 'Flutter Mobile App',
                    category: 'Mobile',
                    description: 'Maintained and improved an existing Flutter/Dart mobile app — fixed bugs, added new features, and integrated it with backend REST APIs.',
                    image: 'https://images.pexels.com/photos/969462/pexels-photo-969462.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Flutter', 'Dart', 'REST API'],
                    demo: null,
                    code: null
                },
                {
                    title: 'Parapharmacy Management System',
                    category: 'Web App',
                    description: 'Developed a web-based management system for a parapharmacy using Laravel — built core backend logic, database features, and delivered based on business needs.',
                    image: 'https://images.pexels.com/photos/13119976/pexels-photo-13119976.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel', 'PHP', 'MySQL'],
                    demo: null,
                    code: null
                },
                {
                    title: 'University Training Evaluation Platform',
                    category: 'Web App',
                    description: 'Graduation project (Master 2) — a web platform connecting companies, students and universities to evaluate and update academic programs in line with the job market.',
                    image: 'https://images.pexels.com/photos/7972324/pexels-photo-7972324.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel 9', 'PHP', 'MySQL', 'Bootstrap', 'JavaScript', 'Ajax'],
                    demo: null,
                    code: null
                },
                {
                    title: 'Medical Web Application',
                    category: 'Web App',
                    description: 'Developed backend functionality, REST APIs, and frontend features for a multi-client medical application as part of the BOOST IT TECH team.',
                    image: 'https://images.pexels.com/photos/19957214/pexels-photo-19957214.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel', 'JavaScript', 'Bootstrap', 'MySQL'],
                    demo: null,
                    code: null
                },
                {
                    title: 'Ticket Reservation Platform',
                    category: 'Web App',
                    description: 'Built a ticket-reservation web platform as part of a multi-client application, adapting functionality to specific client requirements.',
                    image: 'https://images.pexels.com/photos/17527817/pexels-photo-17527817.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel', 'PHP', 'MySQL', 'JavaScript'],
                    demo: null,
                    code: null
                },
                {
                    title: 'Fuel Lab Analysis System',
                    category: 'Web App',
                    description: 'Internship project at NAFTAL — a complete information system to manage fuel lab sample tracking, results control, and automatic report generation.',
                    image: 'https://images.pexels.com/photos/9243563/pexels-photo-9243563.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['PHP', 'MySQL', 'HTML', 'CSS', 'Bootstrap'],
                    demo: null,
                    code: null
                },
                {
                    title: 'Client Website — Psycom Agency',
                    category: 'WordPress',
                    description: 'Designed, developed, and deployed a complete client website end to end at Psycom Agency — from requirements through production via cPanel.',
                    image: 'https://images.pexels.com/photos/256502/pexels-photo-256502.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['WordPress', 'cPanel', 'HTML', 'CSS'],
                    demo: null,
                    code: null
                },
                {
                    title: 'BOOST IT TECH Website',
                    category: 'WordPress',
                    description: 'Built and deployed a WordPress website for BOOST IT TECH from end to end — covering development, configuration, content integration, and production deployment.',
                    image: 'https://images.pexels.com/photos/7325498/pexels-photo-7325498.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['WordPress', 'cPanel', 'PHP'],
                    demo: null,
                    code: null
                }
            ]
        }
    },
    computed: {
        filteredProjects() {
            if (this.activeFilter === 'All') return this.projects;
            return this.projects.filter(p => p.category === this.activeFilter);
        }
    }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: all 0.35s ease;
}

.fade-enter-from {
    opacity: 0;
    transform: translateY(20px) scale(0.98);
}

.fade-leave-to {
    opacity: 0;
    transform: scale(0.98);
}

.fade-leave-active {
    position: absolute;
}
</style>
