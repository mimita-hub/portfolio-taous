<template>
    <section id="skills" ref="sectionRef" class="relative w-full py-24 px-5 sm:px-8 md:px-12 lg:px-8">
        <!-- Background glow -->
        <div class="absolute inset-0 -z-10 overflow-hidden">
            <div class="absolute top-1/4 right-1/4 w-112.5 h-112.5 rounded-full bg-cyan-500/10 blur-[130px]"></div>
            <div class="absolute bottom-1/4 left-1/4 w-112.5 h-112.5 rounded-full bg-pink-500/10 blur-[130px]">
            </div>
        </div>

        <div class="max-w-5xl lg:max-w-7xl mx-auto">

            <!-- Titre -->
            <div class="text-center mb-16">
                <p class="text-cyan-400 text-sm font-semibold uppercase tracking-widest mb-3">
                    Expertise
                </p>
                <h2 class="text-white font-bold text-3xl md:text-4xl lg:text-5xl">
                    My
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400">
                        Skills
                    </span>
                </h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto text-lg">
                    Technologies and tools I use every day.
                </p>
            </div>

            <div class="grid lg:grid-cols-2 gap-12 lg:gap-16 items-start">

                <!-- Barres de compétences -->
                <div class="space-y-7">
                    <h3 class="text-white font-semibold text-xl mb-2 flex items-center gap-2">
                        <span class="w-8 h-px bg-linear-to-r from-pink-400 to-cyan-400"></span>
                        Core Proficiency
                    </h3>
                    <div v-for="skill in skills" :key="skill.name" class="space-y-2">
                        <div class="flex justify-between items-baseline">
                            <span class="text-white font-medium text-sm sm:text-base">{{ skill.name }}</span>
                            <span class="text-cyan-300 text-sm font-semibold">{{ skill.level }}%</span>
                        </div>
                        <div class="relative w-full h-2.5 rounded-full bg-white/10 overflow-hidden">
                            <div class="absolute inset-y-0 left-0 rounded-full bg-linear-to-r from-pink-400 to-cyan-400 transition-all duration-1200 ease-out"
                                :style="{ width: barsVisible ? skill.level + '%' : '0%' }"></div>
                        </div>
                    </div>
                </div>

                <!-- Grille d'outils -->
                <div>
                    <h3 class="text-white font-semibold text-xl mb-6 flex items-center gap-2">
                        <span class="w-8 h-px bg-linear-to-r from-pink-400 to-cyan-400"></span>
                        Tools & Technologies
                    </h3>
                    <div class="grid grid-cols-2 sm:grid-cols-3 gap-4">
                        <div v-for="tool in tools" :key="tool.name"
                            class="group flex flex-col items-center gap-3 p-5 rounded-xl bg-white/5 border border-white/10 hover:border-cyan-400/40 hover:bg-white/[0.07] hover:-translate-y-1 transition-all duration-300">
                            <span class="text-gray-300 group-hover:text-white transition-colors"
                                v-html="tool.icon"></span>
                            <span
                                class="text-gray-300 group-hover:text-white text-xs sm:text-sm text-center font-medium transition-colors">
                                {{ tool.name }}
                            </span>
                        </div>
                    </div>

                    <!-- Currently learning -->
                    <div
                        class="mt-8 p-5 rounded-xl bg-linear-to-r from-cyan-400/10 to-pink-400/10 border border-white/10">
                        <div class="flex items-center gap-3 mb-2">
                            <span
                                class="flex items-center justify-center w-8 h-8 rounded-lg bg-cyan-400/20 border border-cyan-400/30">
                                <svg class="w-4 h-4 text-cyan-300" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                                    stroke-width="2">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
                                </svg>
                            </span>
                            <p class="text-xs uppercase tracking-wider text-gray-400 font-semibold">Currently learning
                            </p>
                        </div>
                        <p class="text-white text-sm">
                            <span class="font-semibold text-cyan-300">React.js</span> — and continuously expanding my
                            modern web development skills.
                        </p>
                    </div>
                </div>

            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Skills',
    data() {
        return {
            barsVisible: false,
            skills: [
                { name: 'PHP / Laravel', level: 90 },
                { name: 'Vue.js', level: 85 },
                { name: 'HTML / CSS / Tailwind', level: 90 },
                { name: 'JavaScript', level: 85 },
                { name: 'MySQL / Oracle', level: 85 },
                { name: 'Java / Python / C / Flutter', level: 65 }
            ],
            tools: [
                {
                    name: 'Vue.js',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 241 207" fill="currentColor"><path d="M120.5 207.4L0 0h48.2l72.3 125.4L192.8 0H241L120.5 207.4z"/><path d="M120.5 165.6L48.2 40.1H96.4l24.1 41.8 24.1-41.8h48.2L120.5 165.6z" fill="rgba(255,255,255,0.3)"/></svg>'
                },
                {
                    name: 'Laravel',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 50 52" fill="currentColor"><path d="M49.6 15.9c-.1-.3-.4-.5-.7-.6-.3-.1-.6 0-.9.2L41 21.5c-.3.3-.4.7-.2 1.1l3.5 8.6c.1.3.1.7-.1 1l-5.2 7.2c-.2.3-.6.4-.9.3l-7.9-2.2c-.4-.1-.7 0-1 .3l-5.2 5.2c-.3.3-.4.7-.2 1.1l4.3 8.6c.2.4.6.6 1 .5l6.5-1.4c.3-.1.6-.3.7-.6L50 16.7c.1-.3 0-.6-.4-.8z"/><path d="M25 0L0 14.4v23.2L25 52l25-14.4V14.4L25 0zm0 6.2l18.8 10.9-18.8 10.9L6.2 17.1 25 6.2z" fill="rgba(255,255,255,0.25)"/></svg>'
                },
                {
                    name: 'PHP',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 50 26" fill="currentColor"><ellipse cx="25" cy="13" rx="24" ry="12" fill="none" stroke="currentColor" stroke-width="2"/><path d="M9 8h4c2 0 3 1 2.5 3.5C15 14 13 15 11 15H9.5l-.5 3H7L9 8zm1.5 2l-.7 3.5h1.7c1 0 1.8-.5 2-1.5.2-1-.3-2-1.3-2h-1.7zM19 8h2l-.5 3h2c1.5 0 2.5.5 2 2.5C24 16 22.5 18 20 18h-3l2-10zm1.5 2l-.7 4h1.7c1 0 1.8-.5 2-2 .2-1-.3-2-1.3-2h-1.7zM28 8h4c2 0 3 1 2.5 3.5C34 14 32 15 30 15h-1.5l-.5 3H26l2-10zm1.5 2l-.7 3.5h1.7c1 0 1.8-.5 2-1.5.2-1-.3-2-1.3-2h-1.7z" fill="rgba(255,255,255,0.25)"/></svg>'
                },
                {
                    name: 'MySQL',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 32 32" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M4 26c2-6 6-18 12-18 3 0 3 4 1 8-1 3-4 6-6 6"/><path d="M16 14c4-2 10-4 12-2 2 2-2 6-6 8"/><path d="M20 10c0-2 1-4 3-4"/><circle cx="26" cy="22" r="3" fill="rgba(255,255,255,0.2)"/></svg>'
                },
                {
                    name: 'JavaScript',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="currentColor"><rect x="0" y="0" width="24" height="24" rx="3" fill="rgba(255,255,255,0.08)"/><path d="M6 18v-2.5c.5.4 1 .5 1.5.5 1 0 1.5-.3 1.5-1V9h2v6c0 2-1 3.5-3.5 3.5-1 0-1.5-.2-2-.5zM12.5 18v-2.2c.3.2.7.3 1.2.3 1 0 1.3-.3 1.3-1.5V9h2v6c0 2.5-1 4-3.5 4-.5 0-1-.1-1.5-.3z" fill="rgba(255,255,255,0.3)"/></svg>'
                },
                {
                    name: 'Bootstrap',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="currentColor"><path d="M3 3h18v18H3z" fill="rgba(255,255,255,0.08)" rx="2"/><path d="M7 7v10h5c2 0 4-1 4-3 0-1.5-1-2.5-2-2.7.8-.3 1.3-1 1.3-2 0-1.5-1-2.3-3-2.3H7zm2.5 1.8h2c.8 0 1.2.3 1.2 1s-.4 1-1.2 1h-2V8.8zm0 3.5h2.2c.9 0 1.3.4 1.3 1.1s-.4 1.1-1.3 1.1H9.5v-2.2z" fill="rgba(255,255,255,0.3)"/></svg>'
                },
                {
                    name: 'WordPress',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="11" fill="rgba(255,255,255,0.08)" stroke="currentColor" stroke-width="0.5"/><path d="M5 12c0 2.5 1.5 4.7 3.5 5.7L5.5 8.5C5.2 9.5 5 10.7 5 12zM12 5c-1 0-2 .2-3 .5l3 8 3-8c-1-.3-2-.5-3-.5zM8 18c1.2.7 2.5 1 4 1s2.8-.3 4-1l-4-10L8 18zM16.5 8.5l-3 8.2C15.5 15.7 17 13.5 17 11c0-.8-.2-1.7-.5-2.5zM12 3c5 0 9 4 9 9s-4 9-9 9-9-4-9-9 4-9 9-9z" fill="rgba(255,255,255,0.3)"/></svg>'
                },
                {
                    name: 'Git / GitHub',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/></svg>'
                },
                {
                    name: 'cPanel',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" fill="rgba(255,255,255,0.08)"/><path d="M7 10h4M7 14h6"/><circle cx="16" cy="10" r="2" fill="rgba(255,255,255,0.25)"/><circle cx="15" cy="15" r="1.5" fill="rgba(255,255,255,0.25)"/></svg>'
                },
                {
                    name: 'XAMPP',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 2L3 7v10l9 5 9-5V7l-9-5z" fill="rgba(255,255,255,0.08)"/><path d="M8 12l4-4 4 4-4 4z" fill="rgba(255,255,255,0.2)"/></svg>'
                },
                {
                    name: 'Flutter',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 256 317" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" xmlns="http://www.w3.org/2000/svg"><path fill="rgba(255,255,255,0.08)" d="M157.7 0L0 157.7l48.7 48.7L255.1 0h-97.4z"/><path fill="rgba(255,255,255,0.08)" d="M157.7 73.1L73.1 157.7l48.7 48.7 84.6-84.6h-48.7z"/><path fill="rgba(255,255,255,0.08)" d="M121.8 194.2l48.7 48.7 48.7-48.7-48.7-48.7-48.7 48.7z"/><path fill="rgba(255,255,255,0.08)" d="M170.5 242.9l48.7 48.7 48.7-48.7-48.7-48.7-48.7 48.7z"/></svg>'
                },


                {
                    name: 'Cloudflare',
                    icon: '<svg class="w-7 h-7" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M17 18a4 4 0 000-8 5 5 0 00-9-1 3 3 0 00-1 6h10z" fill="rgba(255,255,255,0.08)"/><path d="M8 18h10" /></svg>'
                }
            ]
        }
    },
    mounted() {
        const observer = new IntersectionObserver(
            (entries) => {
                if (entries[0].isIntersecting) {
                    this.barsVisible = true;
                    observer.disconnect();
                }
            },
            { threshold: 0.3 }
        );
        observer.observe(this.$el);
    }
}
</script>

<style scoped></style>
