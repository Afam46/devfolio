<template>
     <section id="form" class="mx-auto max-w-4xl px-6 py-24">
        <div class="mb-12 text-center">
            <p class="mb-2 text-sm uppercase tracking-[0.3em] text-cyan-400">
                Форма
            </p>

            <h3 class="text-4xl font-bold">
                Свяжитесь со мной
            </h3>
        </div>

        <form class="space-y-6 rounded-3xl border border-white/10 bg-white/5 p-8">
            <div class="grid gap-6 md:grid-cols-2">
                <input
                    type="text"
                    placeholder="Имя"
                    class="rounded-2xl border border-white/10 bg-[#0f172a] px-5 py-4
                    outline-none transition focus:border-cyan-400"
                >

                <input
                    type="email"
                    placeholder="Email"
                    class="rounded-2xl border border-white/10 bg-[#0f172a] px-5 py-4
                    outline-none transition focus:border-cyan-400"
                >
            </div>

            <input
                type="text"
                placeholder="Телефон"
                class="w-full rounded-2xl border border-white/10 bg-[#0f172a] px-5 py-4
                outline-none transition focus:border-cyan-400"
            >

            <textarea
                rows="5"
                placeholder="Комментарий"
                class="w-full rounded-2xl border border-white/10 bg-[#0f172a] px-5 py-4
                outline-none transition focus:border-cyan-400"
            />

            <button
                class="w-full rounded-2xl bg-cyan-500 py-4 font-semibold text-black transition
                hover:bg-cyan-400"
            >
                Отправить
            </button>
        </form>
    </section>
</template>