<template>
    <nav class="fixed top-0 left-0 w-full z-50 transition-all duration-300"
        :class="scrolled ? 'bg-gray-900/80 backdrop-blur-md border-b border-white/10 py-3' : 'bg-transparent py-5'">
        <div class="max-w-5xl lg:max-w-7xl mx-auto px-5 sm:px-8 md:px-12 lg:px-8 flex items-center justify-between">

            <!-- Logo -->
            <a href="#" class="text-white font-bold text-xl">
                Taous
                <span class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400">DJEDDI</span>
            </a>

            <!-- Liens desktop -->
            <ul class="hidden md:flex items-center gap-8">
                <li v-for="link in links" :key="link.label">
                    <a :href="link.href" class="text-gray-200 hover:text-white transition font-medium relative group">
                        {{ link.label }}
                        <span
                            class="absolute -bottom-1 left-0 w-0 h-0.5 bg-linear-to-r from-pink-400 to-cyan-400 group-hover:w-full transition-all duration-300"></span>
                    </a>
                </li>
            </ul>

            <a href="/cv-taous-djeddi.pdf" download
                class="hidden md:inline-flex items-center gap-2 px-5 py-2 rounded-full bg-linear-to-r from-pink-400 to-cyan-400 text-white font-semibold text-sm hover:opacity-90 transition">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M4 16v2a2 2 0 002 2h12a2 2 0 002-2v-2M7 10l5 5 5-5M12 15V3" />
                </svg>
                Download CV
            </a>

            <!-- Bouton burger mobile -->
            <button @click="menuOpen = !menuOpen" class="md:hidden text-white z-50" aria-label="Menu">
                <svg v-if="!menuOpen" xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                </svg>
                <svg v-else xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
            </button>
        </div>

        <!-- Menu mobile -->
        <transition name="slide">
            <div v-if="menuOpen"
                class="md:hidden fixed inset-0 top-0 bg-gray-900/98 backdrop-blur-md flex flex-col items-center justify-center gap-8">
                <a v-for="link in links" :key="link.label" :href="link.href" @click="menuOpen = false"
                    class="text-white text-2xl font-semibold hover:text-cyan-400 transition">
                    {{ link.label }}
                </a>
                <a href="/cv-taous-djeddi.pdf" download @click="menuOpen = false"
                    class="mt-4 inline-flex items-center gap-2 px-8 py-3 rounded-full bg-linear-to-r from-pink-400 to-cyan-400 text-white font-semibold">
                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="none" viewBox="0 0 24 24"
                        stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M4 16v2a2 2 0 002 2h12a2 2 0 002-2v-2M7 10l5 5 5-5M12 15V3" />
                    </svg>
                    Download CV
                </a>
            </div>
        </transition>
    </nav>
</template>

<script>
export default {
    name: 'NavBar',
    data() {
        return {
            scrolled: false,
            menuOpen: false,
            links: [
                { label: 'Home', href: '#' },
                { label: 'Services', href: '#services' },
                { label: 'Skills', href: '#skills' },
                { label: 'Experience', href: '#experience' },
                { label: 'Projects', href: '#projects' },
                { label: 'Contact', href: '#contact' }
            ]
        }
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll);
    },
    beforeUnmount() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            this.scrolled = window.scrollY > 20;
        }
    }
}
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
    transition: opacity 0.25s ease;
}

.slide-enter-from,
.slide-leave-to {
    opacity: 0;
}
</style>