<template>
    <section
        id="contacts"
        class="py-18"
    >
        <div class="mx-auto max-w-6xl px-6">
            <div class="mb-14 text-center">
                <p
                    class="mb-3 text-sm uppercase tracking-[0.3em] text-cyan-400"
                >
                    Контакты
                </p>

                <h2 class="text-2xl font-bold sm:text-3xl md:text-4xl">
                    Где меня найти
                </h2>

                <p class="mx-auto mt-4 max-w-2xl text-base leading-7 text-gray-400 sm:mt-6 sm:text-lg">
                    Открыт к сотрудничеству, fullstack/backend вакансиям
                    и интересным проектам
                </p>
            </div>

            <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-4">
                <a  v-for="contact in contacts" :key="contact.title"
                    :href="contact.link" target="_blank"
                    class="group rounded-3xl border border-white/10 bg-white/5 p-8
                    transition hover:-translate-y-2 hover:border-cyan-400/40 duration-300"
                >
                    <div
                        class="mb-5 flex h-12 w-12 items-center justify-center
                        rounded-2xl bg-cyan-400/10 text-2xl sm:h-14 sm:w-14 sm:text-3xl"
                    >
                        {{ contact.emoji }}
                    </div>

                    <h3 class="mb-2 text-xl font-semibold sm:text-2xl">
                        {{ contact.title }}
                    </h3>

                    <p class="text-gray-400">
                        {{ contact.desc }}
                    </p>

                    <span
                        class="mt-6 inline-block text-cyan-400 transition group-hover:translate-x-1"
                    >
                        {{ contact.action }}
                    </span>
                </a>
            </div>
        </div>
    </section>
</template>

<script setup>
const contacts = [
    {
        emoji: '💬',
        title: 'Telegram',
        desc: '@afamka',
        link: 'https://t.me/afamka',
        action: 'Написать →',
    },
    {
        emoji: '💻',
        title: 'GitHub',
        desc: 'Мои проекты и код',
        link: 'https://github.com/Afam46',
        action: 'Открыть →',
    },
    {
        emoji: '✉️',
        title: 'Email',
        desc: 'afamka2007@gmail.com',
        link: 'mailto:afamka2007@gmail.com',
        action: 'Отправить →',
    },
    {
        emoji: '📄',
        title: 'Резюме',
        desc: 'Подробнее про опыт',
        link: 'https://docs.google.com/document/d/1GGLN9UGCBC8GcwwsDKYgswuGNz_Wt-_DCb9m1qt8vTo/edit?tab=t.0',
        action: 'Прочитать →',
    },
]
</script>