<template>
    <section id="experience" class="relative w-full py-24 px-5 sm:px-8 md:px-12 lg:px-8">
        <!-- Background glow -->
        <div class="absolute inset-0 -z-10 overflow-hidden">
            <div class="absolute top-1/4 right-1/4 w-100 h-100 rounded-full bg-pink-500/10 blur-[120px]"></div>
            <div class="absolute bottom-1/4 left-1/4 w-100 h-100 rounded-full bg-cyan-500/10 blur-[120px]">
            </div>
        </div>

        <div class="max-w-5xl lg:max-w-6xl mx-auto">

            <!-- Titre -->
            <div class="text-center mb-16">
                <p class="text-cyan-400 text-sm font-semibold uppercase tracking-widest mb-3">
                    Career Path
                </p>
                <h2 class="text-white font-bold text-3xl md:text-4xl lg:text-5xl">
                    Work
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400">
                        Experience
                    </span>
                </h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto text-lg">
                    My professional journey so far.
                </p>
            </div>

            <div class="grid md:grid-cols-[260px_1fr] gap-6 md:gap-10">

                <!-- Liste des entreprises -->
                <div
                    class="flex md:flex-col gap-2 overflow-x-auto md:overflow-visible pb-2 md:pb-0 -mx-1 px-1 md:mx-0 md:px-0 scroll-smooth">
                    <button v-for="(job, index) in experience" :key="job.company" @click="activeIndex = index"
                        class="relative shrink-0 md:shrink text-left px-5 py-4 rounded-xl border transition-all duration-300 whitespace-nowrap md:whitespace-normal"
                        :class="activeIndex === index
                            ? 'bg-white/10 border-cyan-400/50 md:pl-6'
                            : 'bg-white/2 border-white/10 hover:bg-white/5 hover:border-white/20'">
                        <!-- Barre active à gauche (desktop) -->
                        <span v-if="activeIndex === index"
                            class="hidden md:block absolute left-0 top-1/2 -translate-y-1/2 w-1 h-8 rounded-full bg-linear-to-b from-pink-400 to-cyan-400"></span>

                        <p class="font-semibold text-sm"
                            :class="activeIndex === index ? 'text-white' : 'text-gray-300'">
                            {{ job.company }}
                        </p>
                        <p class="text-xs mt-0.5" :class="activeIndex === index ? 'text-cyan-300' : 'text-gray-500'">
                            {{ job.period }}
                        </p>
                    </button>
                </div>

                <!-- Détail du poste sélectionné -->
                <transition name="fade-slide" mode="out-in">
                    <div :key="activeIndex"
                        class="relative rounded-2xl p-6 sm:p-8 bg-white/5 border border-white/10 backdrop-blur-sm min-h-70 overflow-hidden">
                        <!-- Subtle gradient corner -->
                        <div
                            class="absolute top-0 right-0 w-48 h-48 rounded-full bg-cyan-500/5 blur-3xl pointer-events-none">
                        </div>

                        <div class="relative z-10">
                            <!-- Header -->
                            <div class="flex flex-wrap items-start justify-between gap-4 mb-6">
                                <div>
                                    <h3 class="text-white font-bold text-xl sm:text-2xl">
                                        {{ experience[activeIndex].role }}
                                    </h3>
                                    <p
                                        class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400 font-semibold mt-1">
                                        {{ experience[activeIndex].company }}
                                    </p>
                                    <!-- Location -->
                                    <p v-if="experience[activeIndex].location"
                                        class="flex items-center gap-1.5 text-gray-400 text-sm mt-2">
                                        <svg class="w-4 h-4 shrink-0" fill="none" stroke="currentColor"
                                            viewBox="0 0 24 24" stroke-width="1.8">
                                            <path stroke-linecap="round" stroke-linejoin="round"
                                                d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                                            <path stroke-linecap="round" stroke-linejoin="round"
                                                d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                                        </svg>
                                        {{ experience[activeIndex].location }}
                                    </p>
                                </div>
                                <span
                                    class="inline-flex items-center gap-1.5 text-xs font-medium text-gray-400 px-3 py-1.5 rounded-full border border-white/10 bg-white/3 whitespace-nowrap">
                                    <svg class="w-3.5 h-3.5 text-cyan-400" fill="none" stroke="currentColor"
                                        viewBox="0 0 24 24" stroke-width="2">
                                        <path stroke-linecap="round" stroke-linejoin="round"
                                            d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5" />
                                    </svg>
                                    {{ experience[activeIndex].period }}
                                </span>
                            </div>

                            <!-- Tasks -->
                            <ul v-if="experience[activeIndex].tasks" class="space-y-3">
                                <li v-for="task in experience[activeIndex].tasks" :key="task"
                                    class="flex items-start gap-3 text-gray-300 leading-relaxed text-sm sm:text-base">
                                    <span
                                        class="mt-2 w-1.5 h-1.5 rounded-full bg-linear-to-r from-pink-400 to-cyan-400 shrink-0"></span>
                                    <span>{{ task }}</span>
                                </li>
                            </ul>
                            <p v-else class="text-gray-300 leading-relaxed">
                                {{ experience[activeIndex].description }}
                            </p>

                            <!-- Tech stack -->
                            <div v-if="experience[activeIndex].tech" class="mt-6 pt-6 border-t border-white/10">
                                <p class="text-xs uppercase tracking-wider text-gray-500 font-semibold mb-3">Tech Stack
                                </p>
                                <div class="flex flex-wrap gap-2">
                                    <span v-for="t in experience[activeIndex].tech" :key="t"
                                        class="text-xs px-2.5 py-1 rounded-md bg-white/6 border border-white/10 text-gray-300">
                                        {{ t }}
                                    </span>
                                </div>
                            </div>
                        </div>
                    </div>
                </transition>
            </div>

        </div>
    </section>
</template>

<script>
export default {
    name: 'Experience',
    data() {
        return {
            activeIndex: 0,
            experience: [
                {
                    period: '05/2024 - Present',
                    role: 'Freelance Developer',
                    company: 'Freelance',
                    location: 'Algeria',
                    tasks: [
                        'Contributed to the development and maintenance of a Laravel/Vue.js e-commerce platform, building backend features and REST APIs, fixing bugs, and integrating payment and external APIs (Edahabia, Flexy, etc.).',
                        'Maintained and improved an existing Flutter/Dart mobile app, fixing bugs, adding new features, and integrating it with backend REST APIs.',
                        'Developed a parapharmacy management system using Laravel, building core backend logic and database features based on business needs.',
                        'Built and customized WordPress client websites, working on themes, plugins, and content structure.',
                        'Deployed web apps using SSH and Cloudflare, and assisted in mobile releases via Google Play Console.',
                        'Performed functional testing on web and mobile apps, reporting bugs and verifying features before delivery.'
                    ],
                    tech: ['Laravel', 'Vue.js', 'Flutter', 'Dart', 'WordPress', 'MySQL', 'REST API', 'Cloudflare']
                },
                {
                    period: '07/2023 - 02/2024',
                    role: 'Web Developer',
                    company: 'BOOST IT TECH',
                    location: 'Algeria',
                    tasks: [
                        'Developed and maintained Laravel/PHP web applications, implementing new features, fixing bugs, and working with MySQL databases to support business requirements.',
                        'Contributed to a large multi-client web application, developing backend functionality, REST APIs, database operations, and frontend features using JavaScript and Bootstrap.',
                        'Developed web solutions for different business domains, including a medical application and a ticket-reservation platform, adapting functionality to specific client requirements.',
                        'Built and deployed a WordPress website for BOOST IT TECH from end to end, covering development, configuration, content integration, and production deployment.',
                        'Translated client needs into technical solutions, participating in requirements analysis and preparing specifications before development.',
                        'Handled application deployment and maintenance, including cPanel-based deployments and production updates.',
                        'Collaborated on the full software-development lifecycle, from requirements gathering and solution design to development, testing, deployment, and maintenance.'
                    ],
                    tech: ['Laravel', 'PHP', 'JavaScript', 'Bootstrap', 'MySQL', 'WordPress', 'cPanel', 'REST API']
                },
                {
                    period: '03/2023 - 05/2023',
                    role: 'Web Developer',
                    company: 'Psycom Agency',
                    location: 'Algeria',
                    tasks: [
                        'Designed, developed, and deployed a complete client website from end to end, taking ownership of the implementation from requirements through production.',
                        'Developed backend functionality for a second client website, while also implementing frontend updates and integrating requested changes.',
                        'Improved and maintained existing websites, implementing client-requested changes and resolving technical issues.',
                        'Managed website deployments through cPanel, taking projects from development to production.',
                        'Worked across the full web-development lifecycle, including development, testing, updates, and deployment.'
                    ],
                    tech: ['WordPress', 'PHP', 'HTML', 'CSS', 'cPanel']
                },
                {
                    period: '03/2020 - 09/2020',
                    role: 'Software Engineer Intern',
                    company: 'NAFTAL SPA — Fuel Division',
                    location: 'Algeria',
                    tasks: [
                        'Designed and developed a complete web-based information system for managing fuel laboratory analyses as part of a graduation project.',
                        'Developed the application\'s authentication and user-management system, including login and role/user-related functionality.',
                        'Implemented laboratory analysis management and data-entry workflows, replacing manual processes with a centralized digital system.',
                        'Built search and filtering functionality to make laboratory data easier to access and manage.',
                        'Developed dashboards, statistics, and reporting features to support analysis and monitoring.',
                        'Designed and implemented the MySQL database, including the application\'s data structure and CRUD operations.',
                        'Developed the frontend using HTML, CSS, Bootstrap and responsive templates, integrating it with the PHP backend.'
                    ],
                    tech: ['PHP', 'MySQL', 'HTML', 'CSS', 'Bootstrap']
                }
            ]
        }
    }
}
</script>

<style scoped>
.fade-slide-enter-active,
.fade-slide-leave-active {
    transition: all 0.3s ease;
}

.fade-slide-enter-from {
    opacity: 0;
    transform: translateX(12px);
}

.fade-slide-leave-to {
    opacity: 0;
    transform: translateX(-12px);
}
</style>
