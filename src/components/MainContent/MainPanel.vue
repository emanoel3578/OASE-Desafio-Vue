<template>
    <div class="relative flex flex-col gap-8 h-full">
        <div class="flex text-lg justify-center w-full mt-6 gap-3 text-white">
            <button @click="ChangePanel()" class="cursor-pointer hover:underline rounded-full bg-purple-800 p-2">State Machines</button>
            <h1 class="p-2">|</h1>
            <button @click="ChangePanel()" class="cursor-pointer hover:underline p-2 transition duration-150 ease-out hover:ease-in">Ec2</button>
        </div>

        <!-- Current Selected Panel -->
        <div class="h-full" v-if="MainPanelStateMachine">
            <Status />
        </div>

        <div v-else>
            <h1>
                Nada aqui ainda !
            </h1>
        </div>
    </div>
</template>

<script>
import Status from '../MainContent/StatusMachinePanel/Status.vue';
// import Status from '/StatusMachinePanel/Status.vue';

export default {
    name: 'MainPanel',
    data() {
        return {
            MainPanelStateMachine: true
        }
    },
    components: {
        Status
    },
    methods: {
        ChangePanel() {
            this.MainPanelStateMachine = !this.MainPanelStateMachine
            return this.MainPanelStateMachine
        }
        
  }
}

</script>