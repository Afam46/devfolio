<template>
    <section id="form" class="mx-auto max-w-4xl px-6 py-18">
        <div class="mb-12 text-center">
            <p class="mb-2 text-sm uppercase tracking-[0.3em] text-cyan-400">
                Форма
            </p>

            <h3 class="text-2xl font-bold sm:text-3xl md:text-4xl">
                Свяжитесь со мной
            </h3>
        </div>

        <form
            @submit.prevent="submitForm"
            class="space-y-6 rounded-3xl border border-white/10 bg-white/5 p-8
            relative text-sm sm:text-base">
            <div class="grid gap-6 md:grid-cols-2">

                <input
                    v-model="form.name"
                    type="text"
                    placeholder="Имя"
                    class="rounded-2xl border border-white/10 bg-[#0f172a]
                    px-5 py-4 outline-none transition focus:border-cyan-400"
                >

                <input
                    v-model="form.email"
                    type="email"
                    placeholder="Email"
                    class="rounded-2xl border border-white/10 bg-[#0f172a]
                    px-5 py-4 outline-none transition focus:border-cyan-400"
                >
            </div>

            <input
                v-model="form.phone"
                type="text"
                placeholder="Телефон"
                class="w-full rounded-2xl border border-white/10 bg-[#0f172a]
                px-5 py-4 outline-none transition focus:border-cyan-400"
            >

            <textarea
                v-model="form.message"
                rows="5"
                placeholder="Комментарий"
                class="w-full rounded-2xl border border-white/10 bg-[#0f172a]
                px-5 py-4 outline-none transition focus:border-cyan-400"
            />

            <AiBox
                v-if="showAiBox"
                @close="showAiBox = false"
                @error="showError($event)"
                @generated="form.message = $event"
            />
            
            <div class="flex gap-4 flex-row">
                <button
                    :disabled="loading"
                    class="w-full rounded-2xl bg-cyan-500 py-4 font-semibold cursor-pointer
                    text-black transition hover:bg-cyan-400 disabled:opacity-50 sm:py-3"
                >
                    {{ loading ? 'Отправка...' : 'Отправить' }}
                </button>

                <button
                    type="button"
                    @click.stop="showAiBox = !showAiBox"
                    class="rounded-2xl border border-cyan-400 px-6 py-3 text-cyan-400
                    transition hover:bg-[#0f172a] cursor-pointer whitespace-nowrap sm:py-3"
                >
                    ✨ AI
                </button>
            </div>
            <div class="mb-3 h-0.5 w-0.5">
                 <p
                    v-if="successMessage && !errorMessage"
                    class="text-green-400 absolute"
                >
                    {{ successMessage }}
                </p>

                <p
                    v-if="errorMessage"
                    class="text-red-400 absolute"
                >
                    {{ errorMessage }}
                </p>
            </div>
           
        </form>
    </section>
</template>

<script setup>
import axios from 'axios'
import { reactive, ref } from 'vue'
import AiBox from '../../components/AiBox.vue'

const showAiBox = ref(false)

const loading = ref(false)
const successMessage = ref('')
const errorMessage = ref('')
const errorTimeout = ref(null)

const form = reactive({
    name: '',
    email: '',
    phone: '',
    message: '',
})

const submitForm = async () => {

    loading.value = true
 
    try{

        const res = await axios.post('/api/contact', form)

        successMessage.value = res.data.message

        form.name = ''
        form.email = ''
        form.phone = ''
        form.message = ''

        setTimeout(() => { successMessage.value = '' }, 2000)

    }catch(err){

        if(err.response?.status === 422){
            
            showError('Заполните все поля!')
        }else{

            showError('Ошибка отправки формы!')
        }
    }finally{

        loading.value = false
    }
}

const showError = (message) => {

    errorMessage.value = message

    if(errorTimeout.value){
        clearTimeout(errorTimeout.value)
    }

    errorTimeout.value = setTimeout(() => {
        errorMessage.value = ''
    }, 2000)
}
</script>