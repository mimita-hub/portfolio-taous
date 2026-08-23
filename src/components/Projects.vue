<template>
    <section id="projects" class="relative w-full py-24 px-5 sm:px-8 md:px-12 lg:px-8">
        <!-- Background glow -->
        <div class="absolute inset-0 -z-10 overflow-hidden">
            <div class="absolute top-1/3 left-1/4 w-[400px] h-[400px] rounded-full bg-pink-500/10 blur-[120px]"></div>
            <div class="absolute bottom-1/4 right-1/4 w-[400px] h-[400px] rounded-full bg-cyan-500/10 blur-[120px]">
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
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-pink-400 to-cyan-400">
                        Projects
                    </span>
                </h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto text-lg">
                    A selection of recent work — from full-stack platforms to client websites.
                </p>
            </div>

            <!-- Filtres avec compteurs -->
            <div class="flex flex-wrap justify-center gap-3 mb-12">
                <button v-for="cat in categoriesWithCounts" :key="cat.name" @click="activeFilter = cat.name"
                    class="inline-flex items-center gap-2 px-5 py-2 rounded-full text-sm font-medium border transition-all duration-300"
                    :class="activeFilter === cat.name
                        ? 'bg-gradient-to-r from-pink-400 to-cyan-400 text-[#0a0a0f] border-transparent shadow-[0_0_20px_-5px_rgba(34,211,238,0.5)]'
                        : 'text-gray-300 border-white/15 bg-white/[0.03] hover:border-white/30 hover:text-white'">
                    {{ cat.name }}
                    <span class="text-xs px-1.5 py-0.5 rounded-full" :class="activeFilter === cat.name
                        ? 'bg-[#0a0a0f]/20 text-[#0a0a0f]'
                        : 'bg-white/10 text-gray-400'">
                        {{ cat.count }}
                    </span>
                </button>
            </div>

            <!-- Grille de projets -->
            <transition-group tag="div" name="fade" class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
                <article v-for="project in filteredProjects" :key="project.title" @click="openModal(project)"
                    class="group relative rounded-2xl overflow-hidden bg-white/5 border border-white/10 backdrop-blur-sm hover:border-cyan-400/40 transition-all duration-300 hover:-translate-y-2 hover:shadow-[0_20px_40px_-15px_rgba(0,0,0,0.5)] cursor-pointer">
                    <!-- Image -->
                    <div class="relative h-52 overflow-hidden">
                        <img :src="project.image" :alt="project.title" loading="lazy"
                            class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500" />
                        <div class="absolute inset-0 bg-gradient-to-t from-[#0a0a0f] via-[#0a0a0f]/30 to-transparent">
                        </div>

                        <!-- Category badge -->
                        <span
                            class="absolute top-4 left-4 px-3 py-1 rounded-full text-xs font-semibold text-white bg-black/40 backdrop-blur-md border border-white/15">
                            {{ project.category }}
                        </span>

                        <!-- Hover overlay with "View details" -->
                        <div
                            class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300 bg-[#0a0a0f]/40 backdrop-blur-[2px]">
                            <span
                                class="inline-flex items-center gap-2 px-5 py-2.5 rounded-xl text-sm font-semibold text-white bg-white/10 border border-white/20 backdrop-blur-md">
                                View details
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                                    stroke-width="2.5">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                                </svg>
                            </span>
                        </div>
                    </div>

                    <!-- Contenu -->
                    <div class="p-6">
                        <h3 class="text-white font-semibold text-xl mb-3 group-hover:text-cyan-300 transition-colors">
                            {{ project.title }}
                        </h3>
                        <p class="text-gray-300 text-sm leading-relaxed mb-4 line-clamp-3">
                            {{ project.description }}
                        </p>

                        <!-- Tags techno -->
                        <div class="flex flex-wrap gap-2 mb-5">
                            <span v-for="tech in project.stack.slice(0, 4)" :key="tech"
                                class="text-xs px-2.5 py-1 rounded-md bg-white/[0.06] border border-white/10 text-gray-300">
                                {{ tech }}
                            </span>
                            <span v-if="project.stack.length > 4"
                                class="text-xs px-2.5 py-1 rounded-md bg-white/[0.06] border border-white/10 text-gray-400">
                                +{{ project.stack.length - 4 }}
                            </span>
                        </div>

                        <!-- Liens -->
                        <div class="flex gap-4 pt-4 border-t border-white/5" @click.stop>
                            <a v-if="project.demo" :href="project.demo" target="_blank" rel="noopener"
                                class="inline-flex items-center gap-1.5 text-sm font-medium text-white hover:text-pink-400 transition">
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                                    stroke-width="2">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1" />
                                </svg>
                                Live Demo
                            </a>
                            <a v-if="project.code" :href="project.code" target="_blank" rel="noopener"
                                class="inline-flex items-center gap-1.5 text-sm font-medium text-white hover:text-cyan-400 transition">
                                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                                    <path
                                        d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z" />
                                </svg>
                                Source Code
                            </a>
                            <span v-if="!project.demo && !project.code" class="text-sm text-gray-500 italic">
                                Private / NDA project
                            </span>
                        </div>
                    </div>
                </article>
            </transition-group>

            <!-- Empty state -->
            <div v-if="filteredProjects.length === 0" class="text-center py-16">
                <div class="inline-flex flex-col items-center gap-3">
                    <svg class="w-12 h-12 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        stroke-width="1.5">
                        <path stroke-linecap="round" stroke-linejoin="round"
                            d="M20.25 7.5l-.625 10.632a2.25 2.25 0 01-2.247 2.118H6.622a2.25 2.25 0 01-2.247-2.118L3.75 7.5M10 11.25h4M3.375 7.5h17.25c.621 0 1.125-.504 1.125-1.125v-1.5c0-.621-.504-1.125-1.125-1.125H3.375c-.621 0-1.125.504-1.125 1.125v1.5c0 .621.504 1.125 1.125 1.125z" />
                    </svg>
                    <p class="text-gray-400">No projects in this category yet.</p>
                </div>
            </div>

        </div>

        <!-- Modal -->
        <transition name="modal">
            <div v-if="modalProject" @click="closeModal"
                class="fixed inset-0 z-50 flex items-center justify-center p-4 sm:p-6 bg-black/70 backdrop-blur-sm">
                <div @click.stop
                    class="relative w-full max-w-2xl max-h-[90vh] overflow-y-auto rounded-2xl bg-[#12121a] border border-white/10 shadow-2xl">
                    <!-- Close button -->
                    <button @click="closeModal"
                        class="absolute top-4 right-4 z-10 w-9 h-9 flex items-center justify-center rounded-lg bg-white/10 border border-white/10 text-gray-300 hover:text-white hover:bg-white/20 transition">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>

                    <!-- Image banner -->
                    <div class="relative h-56 sm:h-64 overflow-hidden rounded-t-2xl">
                        <img :src="modalProject.image" :alt="modalProject.title" class="w-full h-full object-cover" />
                        <div class="absolute inset-0 bg-gradient-to-t from-[#12121a] via-[#12121a]/40 to-transparent">
                        </div>
                        <span
                            class="absolute top-4 left-4 px-3 py-1 rounded-full text-xs font-semibold text-white bg-black/40 backdrop-blur-md border border-white/15">
                            {{ modalProject.category }}
                        </span>
                    </div>

                    <!-- Content -->
                    <div class="p-6 sm:p-8">
                        <h3 class="text-white font-bold text-2xl mb-3">{{ modalProject.title }}</h3>
                        <p class="text-gray-300 leading-relaxed mb-6">{{ modalProject.description }}</p>

                        <!-- Full tech stack -->
                        <p class="text-xs uppercase tracking-wider text-gray-500 font-semibold mb-3">Tech Stack</p>
                        <div class="flex flex-wrap gap-2 mb-6">
                            <span v-for="tech in modalProject.stack" :key="tech"
                                class="text-sm px-3 py-1.5 rounded-lg bg-white/[0.06] border border-white/10 text-gray-200">
                                {{ tech }}
                            </span>
                        </div>

                        <!-- Links -->
                        <div class="flex flex-wrap gap-4 pt-4 border-t border-white/10">
                            <a v-if="modalProject.demo" :href="modalProject.demo" target="_blank" rel="noopener"
                                class="inline-flex items-center gap-2 px-5 py-2.5 rounded-xl text-sm font-semibold text-[#0a0a0f] bg-gradient-to-r from-pink-400 to-cyan-400 transition hover:scale-[1.02]">
                                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                                    stroke-width="2.5">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M13.828 10.172a4 4 0 00-5.656 0l-4 4a4 4 0 105.656 5.656l1.102-1.101m-.758-4.899a4 4 0 005.656 0l4-4a4 4 0 00-5.656-5.656l-1.1 1.1" />
                                </svg>
                                Live Demo
                            </a>
                            <a v-if="modalProject.code" :href="modalProject.code" target="_blank" rel="noopener"
                                class="inline-flex items-center gap-2 px-5 py-2.5 rounded-xl text-sm font-semibold text-white border border-white/15 bg-white/5 hover:bg-white/10 transition">
                                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                                    <path
                                        d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z" />
                                </svg>
                                Source Code
                            </a>
                            <span v-if="!modalProject.demo && !modalProject.code"
                                class="text-sm text-gray-500 italic self-center">
                                Private / NDA project
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </transition>

    </section>
</template>

<script>
export default {
    name: 'Projects',
    data() {
        return {
            activeFilter: 'All',
            modalProject: null,
            categories: ['All', 'Web App', 'Mobile', 'WebSite'],
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
                    code: 'https://github.com/mimita-hub/diplomajob.git'
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
                /*{
                    title: 'Ticket Reservation Platform',
                    category: 'Web App',
                    description: 'Built a ticket-reservation web platform as part of a multi-client application, adapting functionality to specific client requirements.',
                    image: 'https://images.pexels.com/photos/17527817/pexels-photo-17527817.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel', 'PHP', 'MySQL', 'JavaScript'],
                    demo: null,
                    code: null
                },*/
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
                    title: 'Verrerie Verais',
                    category: 'WebSite',
                    description: 'Designed and developed a complete corporate website for Verrerie Verais as part of Psycom Agency. Built with Laravel and a customized frontend template, the website showcases the company’s glassmaking expertise, product collections, and handcrafted creations through a modern and responsive interface.',
                    image: 'https://www.verais.dz/uploads/produits/1680692872.jpg',
                    stack: ['Laravel', 'PHP', 'Blade', 'HTML', 'CSS', 'JavaScript'],
                    demo: ['https://verais.dz/'],
                    code: null
                },
                {
                    title: 'GFS Promotion',
                    category: 'Website',
                    subType: 'Corporate',
                    description: 'Built the complete backend architecture for GFS Promotion as part of Psycom Agency, handling database design, business logic, content management, data processing, and backend integration from development through production.',
                    image: 'https://images.pexels.com/photos/323780/pexels-photo-323780.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['Laravel', 'PHP', 'MySQL'],
                    demo: 'https://www.gfspromotion.com/',
                    code: null
                },
                {
                    title: 'BOOST IT TECH Website',
                    category: 'WebSite',
                    description: 'Built and deployed a WordPress website for BOOST IT TECH from end to end — covering development, configuration, content integration, and production deployment.',
                    image: 'https://images.pexels.com/photos/7325498/pexels-photo-7325498.jpeg?auto=compress&cs=tinysrgb&h=650&w=940',
                    stack: ['WordPress', 'PHP', 'HTML', 'CSS', 'JavaScript', 'cPanel'],
                    demo: 'https://boostittech.com/wP/',
                    code: null
                }
            ]
        }
    },
    computed: {
        filteredProjects() {
            if (this.activeFilter === 'All') return this.projects;
            return this.projects.filter(p => p.category === this.activeFilter);
        },
        categoriesWithCounts() {
            return this.categories.map(cat => ({
                name: cat,
                count: cat === 'All'
                    ? this.projects.length
                    : this.projects.filter(p => p.category === cat).length
            }));
        }
    },
    methods: {
        openModal(project) {
            this.modalProject = project;
            document.body.style.overflow = 'hidden';
        },
        closeModal() {
            this.modalProject = null;
            document.body.style.overflow = '';
        },
        handleKeydown(e) {
            if (e.key === 'Escape' && this.modalProject) {
                this.closeModal();
            }
        }
    },
    mounted() {
        window.addEventListener('keydown', this.handleKeydown);
    },
    beforeUnmount() {
        window.removeEventListener('keydown', this.handleKeydown);
        document.body.style.overflow = '';
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
    width: 100%;
}

.modal-enter-active,
.modal-leave-active {
    transition: opacity 0.25s ease;
}

.modal-enter-active>div,
.modal-leave-active>div {
    transition: transform 0.25s ease, opacity 0.25s ease;
}

.modal-enter-from,
.modal-leave-to {
    opacity: 0;
}

.modal-enter-from>div,
.modal-leave-to>div {
    transform: scale(0.95) translateY(10px);
    opacity: 0;
}

.line-clamp-3 {
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
}
</style>
