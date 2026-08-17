<template>
    <section id="hero" class="relative min-h-screen w-full overflow-hidden flex items-center">
        <!-- Animated background -->
        <div class="absolute inset-0 -z-10">
            <div class="absolute inset-0 bg-[#0a0a0f]"></div>
            <!-- Grid overlay -->
            <div class="absolute inset-0 opacity-[0.04]"
                style="background-image: linear-gradient(rgba(255,255,255,0.5) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.5) 1px, transparent 1px); background-size: 64px 64px;">
            </div>
            <!-- Glow orbs -->
            <div
                class="absolute top-1/4 -left-32 w-125 h-125 rounded-full bg-cyan-500/20 blur-[120px] animate-pulse-slow">
            </div>
            <div
                class="absolute bottom-1/4 -right-32 w-125 h-125 rounded-full bg-pink-500/15 blur-[120px] animate-pulse-slower">
            </div>
        </div>

        <div class="max-w-7xl mx-auto w-full px-5 sm:px-8 md:px-12 lg:px-8 py-24">
            <div class="grid lg:grid-cols-12 gap-12 items-center">

                <!-- Left: Text content -->
                <div class="lg:col-span-7 space-y-8">
                    <!-- Status badge -->
                    <div
                        class="inline-flex items-center gap-2.5 px-4 py-2 rounded-full border border-white/10 bg-white/5 backdrop-blur-sm">
                        <span class="relative flex h-2.5 w-2.5">
                            <span
                                class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
                            <span class="relative inline-flex rounded-full h-2.5 w-2.5 bg-emerald-400"></span>
                        </span>
                        <span class="text-sm text-gray-300 font-medium">Available for new projects</span>
                    </div>

                    <!-- Name -->
                    <div class="space-y-2">
                        <p class="text-gray-400 text-lg font-medium tracking-wide">Hi, I'm Taous DJEDDI</p>
                        <h1 class="font-bold text-5xl sm:text-6xl lg:text-7xl leading-[1.05] tracking-tight">
                            <span class="block text-white">Full-Stack</span>
                            <span
                                class="block text-transparent bg-clip-text bg-linear-to-r from-pink-400 via-fuchsia-400 to-cyan-400">
                                Developer
                            </span>
                        </h1>
                    </div>

                    <!-- Tagline -->
                    <p class="text-gray-300 text-lg sm:text-xl leading-relaxed max-w-2xl">
                        Based in Algiers, Algeria — I design, build and deploy complete web applications
                        <span class="text-white font-semibold">end to end</span>, from Vue.js front-ends to
                        Laravel and PHP back-ends.
                    </p>

                    <!-- Tech stack pills -->
                    <div class="flex flex-wrap gap-2.5">
                        <span v-for="tech in techStack" :key="tech.name"
                            class="px-3.5 py-1.5 rounded-lg text-sm font-medium border transition-all duration-300 hover:scale-105"
                            :class="tech.active
                                ? 'bg-white/10 border-cyan-400/40 text-white'
                                : 'bg-white/3 border-white/10 text-gray-400 hover:border-white/20 hover:text-gray-200'">
                            {{ tech.name }}
                        </span>
                    </div>

                    <!-- CTAs -->
                    <div class="flex flex-wrap items-center gap-4 pt-2">
                        <a href="#experience"
                            class="group relative inline-flex items-center gap-2 px-7 py-3.5 rounded-xl font-semibold text-sm text-[#0a0a0f] bg-linear-to-r from-pink-400 to-cyan-400 transition-all duration-300 hover:shadow-[0_0_30px_-5px_rgba(34,211,238,0.5)] hover:scale-[1.02]">
                            View my work
                            <svg class="w-4 h-4 transition-transform duration-300 group-hover:translate-x-1" fill="none"
                                stroke="currentColor" viewBox="0 0 24 24" stroke-width="2.5">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                            </svg>
                        </a>
                        <a href="mailto:taousdjeddi98@gmail.com"
                            class="inline-flex items-center gap-2 px-7 py-3.5 rounded-xl font-semibold text-sm text-white border border-white/15 bg-white/5 backdrop-blur-sm transition-all duration-300 hover:bg-white/10 hover:border-white/25">
                            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                            </svg>
                            Get in touch
                        </a>
                    </div>
                </div>

                <!-- Right: Profile card -->
                <div class="lg:col-span-5 lg:justify-self-end w-full max-w-md">
                    <div
                        class="relative rounded-3xl p-8 bg-linear-to-br from-white/[0.07] to-white/2 border border-white/10 backdrop-blur-xl">
                        <!-- Decorative corner gradient -->
                        <div
                            class="absolute -top-px -left-px w-32 h-32 rounded-tl-3xl bg-linear-to-br from-pink-400/30 to-transparent pointer-events-none">
                        </div>

                        <div class="relative space-y-6">
                            <!-- Avatar -->
                            <div class="flex items-center gap-4">
                                <div
                                    class="relative w-16 h-16 rounded-2xl flex items-center justify-center bg-linear-to-br from-pink-400 to-cyan-400 text-2xl font-bold text-[#0a0a0f]">
                                    TD
                                </div>
                                <div>
                                    <p class="text-white font-bold text-lg">Taous DJEDDI</p>
                                    <p class="text-gray-400 text-sm">Software Engineer, M.Sc.</p>
                                </div>
                            </div>

                            <div class="h-px bg-white/10"></div>

                            <!-- Stats -->
                            <div class="grid grid-cols-3 gap-4">
                                <div>
                                    <p class="text-2xl font-bold text-white">4+</p>
                                    <p class="text-xs text-gray-400 mt-0.5">Years coding</p>
                                </div>
                                <div>
                                    <p class="text-2xl font-bold text-white">10+</p>
                                    <p class="text-xs text-gray-400 mt-0.5">Projects shipped</p>
                                </div>
                                <div>
                                    <p class="text-2xl font-bold text-white">∞</p>
                                    <p class="text-xs text-gray-400 mt-0.5">Curiosity</p>
                                </div>
                            </div>

                            <div class="h-px bg-white/10"></div>

                            <!-- Currently learning -->
                            <div>
                                <p class="text-xs uppercase tracking-wider text-gray-500 font-semibold mb-2">
                                    Currently learning
                                </p>
                                <div class="flex items-center gap-2">
                                    <span
                                        class="px-3 py-1 rounded-md text-sm font-medium bg-cyan-400/10 border border-cyan-400/30 text-cyan-300">
                                        React.js
                                    </span>
                                    <span class="text-gray-500 text-sm">+ modern web tooling</span>
                                </div>
                            </div>

                            <div class="h-px bg-white/10"></div>

                            <!-- Contact -->
                            <a href="mailto:taousdjeddi98@gmail.com"
                                class="flex items-center gap-3 text-gray-300 hover:text-white transition-colors group">
                                <span
                                    class="flex items-center justify-center w-9 h-9 rounded-lg bg-white/5 border border-white/10 group-hover:border-cyan-400/40 transition-colors">
                                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                                        stroke-width="2">
                                        <path stroke-linecap="round" stroke-linejoin="round"
                                            d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                                    </svg>
                                </span>
                                <span class="text-sm font-medium">taousdjeddi98@gmail.com</span>
                            </a>
                        </div>
                    </div>
                </div>

            </div>
        </div>

        <!-- Scroll indicator -->
        <div class="absolute bottom-8 left-1/2 -translate-x-1/2 hidden md:flex flex-col items-center gap-2">
            <span class="text-xs text-gray-500 tracking-widest uppercase">Scroll</span>
            <div class="w-px h-10 bg-linear-to-b from-white/30 to-transparent animate-scroll-line"></div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const techStack = ref([
    { name: 'PHP', active: true },
    { name: 'Laravel', active: true },
    { name: 'Vue.js', active: true },
    { name: 'JavaScript', active: false },
    { name: 'MySQL', active: false },
    { name: 'REST APIs', active: false },
    { name: 'Bootstrap', active: false },
    { name: 'Git', active: false },
])
</script>

<style scoped>
@keyframes pulse-slow {

    0%,
    100% {
        opacity: 0.4;
    }

    50% {
        opacity: 0.7;
    }
}

@keyframes pulse-slower {

    0%,
    100% {
        opacity: 0.3;
    }

    50% {
        opacity: 0.55;
    }
}

@keyframes scroll-line {
    0% {
        transform: scaleY(0);
        transform-origin: top;
    }

    45% {
        transform: scaleY(1);
        transform-origin: top;
    }

    55% {
        transform: scaleY(1);
        transform-origin: bottom;
    }

    100% {
        transform: scaleY(0);
        transform-origin: bottom;
    }
}

.animate-pulse-slow {
    animation: pulse-slow 6s ease-in-out infinite;
}

.animate-pulse-slower {
    animation: pulse-slower 8s ease-in-out infinite;
}

.animate-scroll-line {
    animation: scroll-line 2s ease-in-out infinite;
}
</style>
