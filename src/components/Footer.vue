<template>
    <footer id="contact" class="relative w-full pt-24 pb-10 px-5 sm:px-8 md:px-12 lg:px-8 border-t border-white/10">
        <div class="max-w-5xl lg:max-w-7xl mx-auto">

            <!-- Bloc central -->
            <div class="flex flex-col items-center text-center mb-16" data-aos="fade-up">
                <h3 class="text-white font-semibold text-lg mb-6">Find me here too</h3>
                <div class="flex gap-4">
                    <a v-for="social in socials" :key="social.label" :href="social.href" target="_blank" rel="noopener"
                        class="w-12 h-12 flex items-center justify-center rounded-full bg-white/5 border border-white/10 text-gray-200 hover:text-white hover:border-cyan-400/40 hover:-translate-y-1 hover:scale-105 transition-all duration-300"
                        :aria-label="social.label">
                        <span class="flex items-center justify-center" v-html="social.icon"></span>
                    </a>
                </div>
            </div>

            <!-- Bas de page -->
            <div class="flex flex-col md:flex-row items-center justify-between gap-4 pt-8 border-t border-white/10">
                <p class="text-gray-400 text-sm">
                    © {{ currentYear }} Taous DJEDDI. All rights reserved.
                </p>

                <button @click="scrollToTop"
                    class="text-gray-400 hover:text-white text-sm flex items-center gap-2 transition">
                    Back to top
                    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
                    </svg>
                </button>


            </div>

        </div>
    </footer>
</template>

<script>
export default {
    name: 'Footer',
    data() {
        return {
            currentYear: new Date().getFullYear(),
            socials: [
                {
                    label: 'GitHub',
                    href: 'https://github.com/',
                    icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M12 .5C5.73.5.98 5.24.98 11.5c0 4.87 3.16 9 7.55 10.46.55.1.75-.24.75-.53 0-.26-.01-1.13-.02-2.05-3.07.67-3.72-1.3-3.72-1.3-.5-1.28-1.23-1.62-1.23-1.62-1-.69.08-.67.08-.67 1.1.08 1.68 1.13 1.68 1.13.99 1.68 2.58 1.2 3.21.92.1-.72.39-1.2.7-1.47-2.45-.28-5.03-1.22-5.03-5.44 0-1.2.43-2.18 1.13-2.95-.11-.28-.49-1.4.11-2.92 0 0 .93-.3 3.05 1.13.88-.25 1.83-.37 2.77-.37.94 0 1.89.12 2.77.37 2.12-1.43 3.05-1.13 3.05-1.13.6 1.52.22 2.64.11 2.92.7.77 1.13 1.75 1.13 2.95 0 4.23-2.58 5.16-5.04 5.43.4.35.75 1.03.75 2.08 0 1.5-.01 2.71-.01 3.08 0 .29.2.64.76.53A10.52 10.52 0 0 0 23.02 11.5C23.02 5.24 18.27.5 12 .5z"/></svg>'
                },
                {
                    label: 'LinkedIn',
                    href: 'https://www.linkedin.com/in/taous-djeddi-7475491a6/', // TODO: replace with your exact LinkedIn URL
                    icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M20.45 20.45h-3.55v-5.57c0-1.33-.02-3.04-1.85-3.04-1.86 0-2.15 1.45-2.15 2.94v5.67H9.35V9h3.41v1.56h.05c.47-.9 1.63-1.85 3.36-1.85 3.6 0 4.27 2.37 4.27 5.45v6.29zM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12zM7.11 20.45H3.56V9h3.55v11.45zM22.22 0H1.77C.8 0 0 .78 0 1.75v20.5C0 23.22.8 24 1.77 24h20.45c.98 0 1.78-.78 1.78-1.75V1.75C24 .78 23.2 0 22.22 0z"/></svg>'
                },
                {
                    label: 'Email',
                    href: 'mailto:taousdjeddi98@gmail.com',
                    icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" /></svg>'
                }
            ]
        }
    },
    methods: {
        scrollToTop() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    }
}
</script>

<style></style>