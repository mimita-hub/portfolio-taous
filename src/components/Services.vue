<template>
    <section id="services" class="relative w-full py-24 px-5 sm:px-8 md:px-12 lg:px-8">
        <!-- Background glow -->
        <div class="absolute inset-0 -z-10 overflow-hidden">
            <div class="absolute top-1/3 left-1/3 w-100 h-100 rounded-full bg-pink-500/10 blur-[120px]"></div>
            <div class="absolute bottom-1/4 right-1/4 w-100 h-100 rounded-full bg-cyan-500/10 blur-[120px]">
            </div>
        </div>

        <div class="max-w-5xl lg:max-w-7xl mx-auto">

            <!-- Titre de section -->
            <div class="text-center mb-16">
                <p class="text-cyan-400 text-sm font-semibold uppercase tracking-widest mb-3">
                    What I Offer
                </p>
                <h2 class="text-white font-bold text-3xl md:text-4xl lg:text-5xl">
                    My
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400">
                        Services
                    </span>
                </h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto text-lg">
                    What I can do to bring your projects to life.
                </p>
            </div>

            <!-- Grille de cartes -->
            <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
                <div v-for="service in services" :key="service.title"
                    class="group relative rounded-2xl p-8 bg-white/5 border border-white/10 backdrop-blur-sm hover:border-cyan-400/40 hover:-translate-y-2 hover:shadow-[0_20px_40px_-15px_rgba(0,0,0,0.5)] transition-all duration-300">
                    <!-- Halo au hover -->
                    <div
                        class="absolute inset-0 rounded-2xl bg-linear-to-br from-pink-400/10 to-cyan-400/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none">
                    </div>

                    <div class="relative z-10">
                        <!-- Icon -->
                        <div
                            class="w-14 h-14 flex items-center justify-center rounded-xl bg-linear-to-br from-pink-400 to-cyan-400 mb-6 group-hover:scale-110 transition-transform duration-300">
                            <span class="text-[#0a0a0f]" v-html="service.icon"></span>
                        </div>

                        <h3 class="text-white font-semibold text-xl mb-3 group-hover:text-cyan-300 transition-colors">
                            {{ service.title }}
                        </h3>
                        <p class="text-gray-300 leading-relaxed text-sm">
                            {{ service.description }}
                        </p>

                        <!-- Feature list -->
                        <ul class="mt-5 space-y-2">
                            <li v-for="feature in service.features" :key="feature"
                                class="flex items-center gap-2 text-sm text-gray-400">
                                <svg class="w-4 h-4 text-cyan-400 shrink-0" fill="none" stroke="currentColor"
                                    viewBox="0 0 24 24" stroke-width="2.5">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                                </svg>
                                {{ feature }}
                            </li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- CTA -->
            <div class="mt-16 text-center">
                <div
                    class="inline-flex flex-col sm:flex-row items-center gap-4 p-6 sm:p-8 rounded-2xl bg-linear-to-r from-white/5 to-white/2 border border-white/10 backdrop-blur-sm">
                    <p class="text-gray-300 text-lg">
                        Have a project in mind? Let's build it together.
                    </p>
                    <a href="mailto:taousdjeddi98@gmail.com"
                        class="inline-flex items-center gap-2 px-6 py-3 rounded-xl font-semibold text-sm text-[#0a0a0f] bg-linear-to-r from-pink-400 to-cyan-400 transition-all duration-300 hover:scale-[1.03] hover:shadow-[0_0_25px_-5px_rgba(34,211,238,0.5)] whitespace-nowrap">
                        Start a project
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2.5">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                        </svg>
                    </a>
                </div>
            </div>

        </div>
    </section>
</template>

<script>
export default {
    name: 'Services',
    data() {
        return {
            services: [
                {
                    icon: '<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M9 17.25v1.007a3 3 0 01-.879 2.122L7.5 21h9l-.621-.621A3 3 0 0115 18.257V17.25m6-3V4.5a2.25 2.25 0 00-2.25-2.25H5.25A2.25 2.25 0 003 4.5v9.75m18 0H3m18 0a2.25 2.25 0 01-2.25 2.25H5.25A2.25 2.25 0 013 14.25z"/></svg>',
                    title: 'Full-Stack Development',
                    description: 'End-to-end web applications built with Vue.js on the front-end and Laravel/PHP on the back-end.',
                    features: ['Front-end + back-end', 'REST API integration', 'Database design']
                },
                {
                    icon: '<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.375zM7.5 7.5c0-.621.504-1.125 1.125-1.125S9.75 6.879 9.75 7.5 9.246 8.625 8.625 8.625 7.5 8.121 7.5 7.5z"/><path stroke-linecap="round" stroke-linejoin="round" d="M9.75 15.002a3 3 0 0 0-1.5-5.82 3 3 0 0 0 1.5 5.82zM3 3l18 18"/></svg>',
                    title: 'Front-End Development',
                    description: 'Responsive, modern interfaces with Vue.js, Tailwind CSS and Bootstrap.',
                    features: ['Responsive design', 'Component architecture', 'Smooth animations']
                },
                {
                    icon: '<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M9.594 3.94c.09-.542.56-.94 1.11-.94h2.593c.55 0 1.02.398 1.11.94l.213 1.281c.063.374.313.686.645.87.074.04.147.083.22.127.324.196.72.257 1.075.124l1.217-.456a1.125 1.125 0 011.37.49l1.296 2.247a1.125 1.125 0 01-.26 1.431l-1.003.827c-.293.24-.438.613-.431.992a6.75 6.75 0 010 .255c-.007.378.138.75.43.99l1.005.828c.424.35.534.954.26 1.43l-1.298 2.247a1.125 1.125 0 01-1.369.491l-1.217-.456c-.355-.133-.75-.072-1.076.124a6.57 6.57 0 01-.22.128c-.331.183-.581.495-.644.869l-.213 1.28c-.09.543-.56.941-1.11.941h-2.594c-.55 0-1.02-.398-1.11-.94l-.213-1.281c-.062-.374-.312-.686-.644-.87a6.52 6.52 0 01-.22-.127c-.325-.196-.72-.257-1.076-.124l-1.217.456a1.125 1.125 0 01-1.369-.49l-1.297-2.247a1.125 1.125 0 01.26-1.431l1.004-.827c.292-.24.437-.613.43-.992a6.932 6.932 0 010-.255c.007-.378-.138-.75-.43-.99l-1.004-.828a1.125 1.125 0 01-.26-1.43l1.297-2.247a1.125 1.125 0 011.37-.491l1.216.456c.356.133.75.072 1.076-.124.072-.044.146-.087.22-.128.332-.183.582-.495.644-.869l.214-1.281z"/><path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/></svg>',
                    title: 'Back-End & APIs',
                    description: 'Building and consuming REST APIs with PHP, Laravel, Java and Python.',
                    features: ['REST API design', 'Authentication systems', 'Third-party integrations']
                },
                {
                    icon: '<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M20.25 6.375c0 2.278-3.694 4.125-8.25 4.125S3.75 8.653 3.75 6.375m16.5 0c0-.621-.504-1.125-1.125-1.125h-9.75c-.621 0-1.125.504-1.125 1.125m16.5 0v11.25c0 .621-.504 1.125-1.125 1.125H5.625c-.621 0-1.125-.504-1.125-1.125V6.375M3.75 6.375v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V6.375"/><path stroke-linecap="round" stroke-linejoin="round" d="M12 10.5v6m-3-3h6"/></svg>',
                    title: 'Database Design',
                    description: 'Schema design and management with MySQL and Oracle.',
                    features: ['Schema architecture', 'CRUD operations', 'Query optimization']
                },
                {
                    icon: '<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M15.59 14.37a6 6 0 01-5.84 7.48v-2.98m7.08-4.5a6 6 0 00-5.84-6.48v2.98M12 2a10 10 0 11-10 10 10 10 0 0110-10z"/><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 13.5a8.25 8.25 0 0 0 12 7.5M19.5 10.5a8.25 8.25 0 0 0-12-7.5"/></svg>',
                    title: 'Deployment & DevOps',
                    description: 'Deploying and maintaining projects on cPanel, Cloudflare, and via SSH.',
                    features: ['Production deployment', 'Cloudflare setup', 'Google Play releases']
                },
                {
                    icon: '<svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9s-2.015-9-4.5-9m0 18c-2.485 0-4.5-4.03-4.5-9s2.015-9 4.5-9m0 0a9.004 9.004 0 018.716 6.747M12 3a9.004 9.004 0 00-8.716 6.747m17.432 0a9 9 0 010 5.506m-17.432 0a9 9 0 000-5.506"/></svg>',
                    title: 'CMS & Websites',
                    description: 'WordPress websites and custom solutions tailored to client needs.',
                    features: ['WordPress development', 'Theme customization', 'Content integration']
                }
            ]
        }
    }
}
</script>

<style scoped></style>
