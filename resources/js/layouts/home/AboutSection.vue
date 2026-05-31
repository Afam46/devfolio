<template>
    <section id="about" class="mx-auto max-w-6xl px-6 py-24">
        <div class="mb-12">
            <p class="mb-2 text-sm uppercase tracking-[0.3em] text-cyan-400">
                Обо мне
            </p>

            <h3 class="text-2xl font-bold sm:text-3xl md:text-4xl">
                Стек и подход к разработке
            </h3>
        </div>

        <div class="grid gap-6 md:grid-cols-2">
            <div class="rounded-3xl border border-white/10 bg-white/5 p-8">
                <h4 class="mb-4 text-xl font-semibold sm:text-2xl">
                    Как я работаю
                </h4>

                <p  class="text-sm leading-7 text-gray-300 sm:text-base sm:leading-8">
                    Люблю аккуратную архитектуру, понятный код и
                    автоматизацию. Использую AI-инструменты для ускорения
                    разработки, генерации идей и рефакторинга
                </p>
            </div>

            <div class="rounded-3xl border border-white/10 bg-white/5 p-8">
                <h4 class="mb-4 text-xl font-semibold sm:text-2xl">
                    Технологии
                </h4>

                <div class="flex flex-wrap gap-3">
                    <span
                        v-for="item in stack"
                        :key="item"
                        class="rounded-full border border-cyan-400/20 bg-cyan-400/10 px-4 py-2
                        sm:text-sm text-cyan-300 text-xs"
                    >
                        {{ item }}
                    </span>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>

const stack = [
    'Laravel',
    'PHP',
    'Vue 3',
    'JavaScript',
    'MySQL',
    'Redis',
    'Docker',
    'REST API',
    'Linux',
    'PHPUnit',
]

</script>