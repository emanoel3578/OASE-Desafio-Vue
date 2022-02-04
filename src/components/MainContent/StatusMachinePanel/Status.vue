<template>
    <div class="h-full text-white">
        <div class="flex flex-col bottom-0 h-full items-center">

            <div class="h-1/5 mb-8 flex flex-col items-center justify-center">
                <h1 class="text-3xl" @click="ApiCall()">Status das minhas maquinas</h1>
            </div>

            <div class="flex flex-col gap-6 w-full items-center">
                <div class="flex w-4/5 items-center rounded-full justify-between px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="h-14" src="../../../../public/assets/computer.png" alt="">
                    <h1> Meu nome </h1>
                    <h1> Minha instancia </h1>
                    <h1> Placeholder </h1>
                </div>

                <div class="flex w-4/5 items-center rounded-full justify-between px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="h-14" src="../../../../public/assets/computer.png" alt="">
                    <h1> Meu nome </h1>
                    <h1> Minha instancia </h1>
                    <h1> Placeholder </h1>
                </div>

                <div class="flex w-4/5 items-center rounded-full justify-between px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="h-14" src="../../../../public/assets/computer.png" alt="">
                    <h1> Meu nome </h1>
                    <h1> Minha instancia </h1>
                    <h1> Placeholder </h1>
                </div>

                <div class="flex w-4/5 items-center rounded-full justify-between px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="h-14" src="../../../../public/assets/computer.png" alt="">
                    <h1> Meu nome </h1>
                    <h1> Minha instancia </h1>
                    <h1> Placeholder </h1>
                </div>

                <div class="flex w-4/5 items-center rounded-full justify-between px-8 bg-gray-600 border-4 border-purple-400">
                    <img class="h-14" src="../../../../public/assets/computer.png" alt="">
                    <h1> Meu nome </h1>
                    <h1> Minha instancia </h1>
                    <h1> Placeholder </h1>
                </div>
            </div>

            <div class="flex mt-10 justify-center text-white text-xl gap-4">
                <h1>1</h1>
                <h1>2</h1>
                <h1>3</h1>
                <h1>4</h1>
                <h1>5</h1>
                <h1>6</h1>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Status',
    data() {
        return {
            info: "",
        }
    },
    methods: {
    ApiCall() {
      axios.get('http://127.0.0.1:8000/api/listStateMachines').then(
      response =>(this.info = response),
      console.log(this.info.data))
    }
  }
}
</script>