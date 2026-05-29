<template>
     <section id="projects" class="bg-[#111827] py-24">
        <div class="mx-auto max-w-6xl px-6">
            <div class="mb-12">
                <p class="mb-2 text-sm uppercase tracking-[0.3em] text-cyan-400">
                    Проекты
                </p>

                <h3 class="text-4xl font-bold">
                    Кейсы и опыт
                </h3>
            </div>

            <div class="grid gap-6 md:grid-cols-3">
                <div
                    v-for="project in projects"
                    :key="project.title"
                    class="rounded-3xl border border-white/10 bg-white/5 p-6 transition
                    hover:-translate-y-2 hover:border-cyan-400/30"
                >
                    <h4 class="mb-4 text-2xl font-semibold">
                        {{ project.title }}
                    </h4>

                    <p class="mb-6 leading-7 text-gray-300">
                        {{ project.description }}
                    </p>

                    <span class="text-sm text-cyan-400">
                        {{ project.tech }}
                    </span>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>

const projects = [
    {
        title: 'AI Telegram Bot',
        description: 'AI-ассистент с задачами, импортом Excel, очередями и интеграциями API.',
        tech: 'Laravel, Redis, MySQL, Telegram API'
    },
    {
        title: 'Nitro Rush',
        description: 'Мультиплеерная браузерная игра с WebSocket и кешированием.',
        tech: 'Laravel Reverb, Vue, Redis'
    },
    {
        title: 'Devfolio',
        description: 'Frontend + API тестовое задание с AI-интеграцией.',
        tech: 'Vue, Laravel API, OpenAI'
    }
]

</script>