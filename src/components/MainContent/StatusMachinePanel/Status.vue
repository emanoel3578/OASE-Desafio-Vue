<template>
    <div class="h-full text-white">
        <div class="flex flex-col bottom-0 h-full items-center">

            <div class="h-1/5 mb-8 flex flex-col items-center justify-center">
                <h1 class="text-3xl">Status das minhas maquinas</h1>
            </div>

            <div class="flex flex-col items-end mb-2 mr-8 w-4/5">
                <h1 class="text-white text-sm">
                    Ultima atualização: {{this.lastUpdate}}
                </h1>
            </div>

            <div class="flex flex-col gap-6 w-full items-center">
                <div v-for="item in stateMachines" :key="item.name" class="flex flex-row w-4/5 justify-between items-center rounded-full px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="ml-5 h-14" src="../../../../public/assets/computer.png" alt="">
                    <h1 class="w-4/5 pl-4"> {{item.name}} </h1>
                    <h1 class="w-3/5 pl-4"> {{item.type}} </h1>
                    <h1 class="w-2/5 pl-4 text-green-400"> {{item.status}} </h1>
                </div>
            </div>

            <div class="flex w-4/5 mt-20 justify-between text-white text-xl gap-4">
                <button class="cursor-not-allowed">
                    <img src="../../../../public/assets/arrow.png" class="h-12 w-12" alt="">
                </button>

                <button class="cursor-not-allowed">
                    <img src="../../../../public/assets/arrow.png" class="disabled transform rotate-180 h-12 w-12" alt="">
                </button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Status',
    props:['stateMachines','lastUpdate'],
    data() {
        return {
            info: "",
        }
    },
    methods: {
        async Apicall() {
            try{
                await axios.get('http://127.0.0.1:8000/api/listStateMachines')
            }catch(e) {
                console.error(e)
            }
        }
    },
}
</script>