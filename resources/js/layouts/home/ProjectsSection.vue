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

            <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
                <a
                    v-for="project in visibleProjects"
                    :key="project.title"
                    :href="project.link"
                    target="_blank"
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
                </a>
            </div>
            <div class="mt-10 text-center">
                <a
                    @click="showAll = !showAll"
                    href="#projects"
                    class="rounded-2xl border border-cyan-400 px-8 py-4
                    text-cyan-400 transition hover:bg-cyan-400
                    hover:text-black cursor-pointer"
                >
                    {{ showAll ? 'Скрыть проекты' : 'Показать все проекты' }}
                </a>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'

const showAll = ref(false)
const projectsPerRow = ref(3)

const projects = [
    {
        title: 'AI Telegram Bot',
        description: 'AI-ассистент с задачами, Excel, очередями и API',
        tech: 'Laravel, Redis, MySQL, API',
        link: 'https://github.com/Afam46/tg_bot'
    },
    {
        title: 'Nitro Rush',
        description: 'Гоночная браузерная игра с WebSocket и кешированием',
        tech: 'Laravel Reverb, Vue, Redis',
        link: 'https://github.com/Afam46/Nitro-Rush'
    },
    {
        title: 'Afolio',
        description: 'Frontend + API тестовое задание с AI-интеграцией',
        tech: 'Vue, Laravel API, OpenAI',
        link: 'https://github.com/Afam46/afolio'
    },
    {
        title: 'WB API Importer',
        description: 'Импорт данных из API Wildberries по ключу',
        tech: 'Laravel, MySQL, WB API, Postman',
        link: 'https://github.com/Afam46/wb-importer'
    },
    {
        title: 'Garden Goldmine',
        description: 'Веб-приложение для выращивания растений',
        tech: 'Laravel, Vue, MySQl, AdminLTE',
        link: 'https://github.com/Afam46/Garden-Goldmine'
    },
    {
        title: 'Space War',
        description: 'Космический раннер с видом сверху на игровом движке',
        tech: 'Godot, GDScript, Aseprite',
        link: 'https://github.com/Afam46/Space-War'
    }
]

const updateProjectsCount = () => {

    if(window.innerWidth >= 1024){
        projectsPerRow.value = 3
    }else{
        projectsPerRow.value = 2
    }
}

onMounted(() => {

    updateProjectsCount()

    window.addEventListener('resize', updateProjectsCount)
})

onBeforeUnmount(() => {

    window.removeEventListener('resize', updateProjectsCount)
})

const visibleProjects = computed(() => {

    if(showAll.value){
        return projects
    }

    return projects.slice(0, projectsPerRow.value)
})
</script>