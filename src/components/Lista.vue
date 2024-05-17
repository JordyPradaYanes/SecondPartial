<script setup>
import { ref } from "vue"

const indice = ref(0)

const temas = [{title: 'Tema 1',desc: 'texto tema 1'}
    ,{title: 'Tema 2',desc: 'texto tema 2'}
    ,{title: 'Tema 3',desc: 'texto tema 3'}
    ,{title: 'Tema 4',desc: 'texto tema 4'}]

function changeIndex(index) {
    if (indice.value == index) {
        indice.value = -1
    } else {
        indice.value = index
    }
}

</script>

<template>
    <main class="h-screen flex justify-center items-center">
        <section class="bg-blue-300 w-full max-w-xl flex flex-col gap-4 p-3">
            <div class="flex flex-col gap-2" v-for="(tema, index) in temas">
                <button @click="changeIndex(index)" class="bg-blue-100 flex  justify-between px-5 py-2 select-none">
                    <p>
                        {{ tema.title }}
                    </p>

                    <p v-if="index != indice">X</p>
                    <p v-else>-</p>
                </button>

                <div class="min-h-40 bg-slate-100 p-4" v-if="index == indice">
                    {{ tema.desc }}
                </div>
            </div>
        </section>
    </main>
</template>