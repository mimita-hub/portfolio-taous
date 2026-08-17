<template>
    <section id="contact" class="relative w-full py-24 px-5 sm:px-8 md:px-12 lg:px-8">
        <div class="max-w-3xl mx-auto">

            <!-- Titre -->
            <div class="text-center mb-12" data-aos="fade-up">
                <h2 class="text-white font-bold text-3xl md:text-4xl lg:text-5xl">
                    Get in
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-pink-400 to-cyan-400">
                        Touch
                    </span>
                </h2>
                <p class="text-gray-300 mt-4 text-lg">
                    Have an idea, a project, or just a question? Send me a message.
                </p>
            </div>

            <!-- Formulaire -->
            <form @submit.prevent="handleSubmit"
                class="rounded-2xl p-8 bg-white/5 border border-white/10 backdrop-blur-sm space-y-6" data-aos="fade-up"
                data-aos-delay="100">
                <div class="grid sm:grid-cols-2 gap-6">
                    <div>
                        <label for="name" class="block text-sm font-medium text-gray-200 mb-2">Name</label>
                        <input id="name" v-model="form.name" type="text" required placeholder="Your name"
                            class="w-full px-4 py-3 rounded-lg bg-white/5 border border-white/10 text-white placeholder-gray-500 focus:outline-none focus:border-pink-400/50 transition" />
                    </div>
                    <div>
                        <label for="email" class="block text-sm font-medium text-gray-200 mb-2">Email</label>
                        <input id="email" v-model="form.email" type="email" required placeholder="you@example.com"
                            class="w-full px-4 py-3 rounded-lg bg-white/5 border border-white/10 text-white placeholder-gray-500 focus:outline-none focus:border-cyan-400/50 transition" />
                    </div>
                </div>

                <div>
                    <label for="subject" class="block text-sm font-medium text-gray-200 mb-2">Subject</label>
                    <input id="subject" v-model="form.subject" type="text" required placeholder="What's this about?"
                        class="w-full px-4 py-3 rounded-lg bg-white/5 border border-white/10 text-white placeholder-gray-500 focus:outline-none focus:border-pink-400/50 transition" />
                </div>

                <div>
                    <label for="message" class="block text-sm font-medium text-gray-200 mb-2">Message</label>
                    <textarea id="message" v-model="form.message" rows="5" required placeholder="Your message..."
                        class="w-full px-4 py-3 rounded-lg bg-white/5 border border-white/10 text-white placeholder-gray-500 focus:outline-none focus:border-cyan-400/50 transition resize-none"></textarea>
                </div>

                <button type="submit" :disabled="sending"
                    class="w-full sm:w-auto px-8 py-3 rounded-full bg-linear-to-r from-pink-400 to-cyan-400 text-white font-semibold hover:opacity-90 transition disabled:opacity-50 disabled:cursor-not-allowed">
                    {{ sending ? 'Sending...' : 'Send Message' }}
                </button>

                <p v-if="status === 'success'" class="text-green-400 text-sm">
                    ✅ Message sent successfully, I'll get back to you soon!
                </p>
                <p v-if="status === 'error'" class="text-red-400 text-sm">
                    ❌ Something went wrong, please try again or email me directly.
                </p>
            </form>

        </div>
    </section>
</template>

<script>
export default {
    name: 'Contact',
    data() {
        return {
            form: {
                name: '',
                email: '',
                subject: '',
                message: ''
            },
            sending: false,
            status: null
        }
    },
    methods: {
        async handleSubmit() {
            this.sending = true;
            this.status = null;

            try {
                // Remplace par ton propre endpoint (Formspree, EmailJS, ton API, etc.)
                // Exemple avec Formspree :
                // await fetch('https://formspree.io/f/TON_ID', {
                //   method: 'POST',
                //   headers: { 'Content-Type': 'application/json' },
                //   body: JSON.stringify(this.form)
                // });

                await new Promise(resolve => setTimeout(resolve, 1000)); // simulation

                this.status = 'success';
                this.form = { name: '', email: '', subject: '', message: '' };
            } catch (error) {
                this.status = 'error';
            } finally {
                this.sending = false;
            }
        }
    }
}
</script>

<style></style>