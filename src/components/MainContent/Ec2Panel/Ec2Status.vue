<template>
    <div>
        <div class="h-full text-white">
        <div class="flex flex-col bottom-0 h-full items-center">

            <div class="my-10 flex flex-col items-center justify-center">
                <h1 class="text-3xl" @click="asdo()">Instancias em EC2</h1>
            </div>

            <div class="flex flex-col items-end mb-2 mr-8 w-4/5">
                <h1 class="text-white text-sm">
                    Ultima atualização: {{ecUpdate}}
                </h1>
            </div>

            <div class="flex flex-col gap-6 w-full items-center">
                <div v-for="item in ecInstance" :key="item.name" class="flex gap-14 w-4/5 items-center rounded-full px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="h-14 -mr-10" src="../../../../public/assets/cloud.png" alt="">
                    <h1 class="w-1/5"> {{item.instance_id}} </h1>
                    <h1 class="w-1/5"> {{item.instance_type}} </h1>
                    <h1 class="w-1/5"> {{item.ipv4}} </h1>
                    <h1 class="w-1/5"> {{item.dns}}</h1>
                    <h1 class="text-green-400"> {{item.status}} </h1>
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
    </div>
</template>

<script>
export default {
    name:'Ec2Status',
    props: ['ecInstance', 'ecUpdate'],
    data () {
        return {
        }
    },
    methods: {
        asdo() {
            console.log(this.ecInstance)
        }
    }
}
</script>