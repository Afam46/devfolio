<template>
     <section class="mx-auto flex min-h-[85vh] max-w-6xl flex-col justify-center px-6">
        <div
            class="max-w-3xl transition-all duration-1000"
            :class="loaded ? 'translate-x-0 opacity-100' : '-translate-x-16 opacity-0'"
        >
            <p class="mb-4 text-sm uppercase tracking-[0.3em] text-cyan-400">
                Fullstack Developer
            </p>

            <h2 class="mb-6 text-3xl font-bold leading-tight sm:text-5xl md:text-6xl z-30">
                Привет, я Ислам
                <span class="inline-block animate-wave transition-all duration-1000"
                :class="loaded ? 'translate-x-0 opacity-100' : '-translate-x-16 opacity-0'"
                >👋</span>
            </h2>

            <p class="mb-8 text-base leading-7 text-gray-300 sm:text-lg sm:leading-8">
                Fullstack-разработчик с фокусом на Laravel + Vue.
                Разрабатываю API, Telegram-ботов, realtime-приложения,
                AI-интеграции и современные SPA
            </p>

            <div class="flex gap-4 flex-row">
                <a
                    href="#projects"
                    class="inline-flex items-center justify-center rounded-xl
                    bg-cyan-500 px-4 py-2 text-center text-sm font-medium transition
                    hover:bg-cyan-400 duration-300 sm:px-6 sm:py-3"
                >
                    Мои проекты
                </a>
                <a
                    href="#form"
                    class="inline-flex items-center justify-center rounded-xl
                    border border-white/20 px-4 py-2 text-center text-sm font-medium transition
                    hover:border-cyan-400 duration-300 hover:text-cyan-400 sm:px-6 sm:py-3"
                >
                    Связаться
                </a>
            </div>
        </div>
    </section>
</template>

<script setup>

import { ref, onMounted } from 'vue'

const loaded = ref(false)

onMounted(() => {
    setTimeout(() => {
        loaded.value = true
    }, 200)
})

</script>