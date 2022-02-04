<template>
    <div class="relative flex flex-col gap-8 h-full">
        <div class="flex text-lg justify-center w-full mt-6 gap-3 text-white">
            <button @click="ChangePanel($event)" :class="{'bg-purple-800': MainPanelStateMachine}" class="transform transition ease-in-out delay-150 p-2 rounded-full hover:-translate-y-1 hover:scale-110 duration-300">State Machines</button>
            <h1 class="p-2">|</h1>
            <button @click="ChangePanel($event)" :class="{'bg-purple-800': Ec2Panel}" class="transform transition ease-in-out delay-150  p-2 rounded-full hover:-translate-y-1 hover:scale-110 duration-300">Ec2</button>
        </div>

        <!-- Current Selected Panel -->
        <div class="h-full" v-if="MainPanelStateMachine">
            <Status :stateMachines="stateMachines" :lastUpdate="lastUpdate" />
        </div>

        <div class="h-full" v-else>
            <h1>
                <Ec2Status :ecInstance="ecInstance" :ecUpdate="ecUpdate" />
            </h1>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import Status from '../MainContent/StatusMachinePanel/Status.vue';
import Ec2Status from '../MainContent/Ec2Panel/Ec2Status.vue';

export default {
    name: 'MainPanel',
    data() {
        return {
            Ec2Panel: false,
            MainPanelStateMachine: true,
            stateMachines: [],
            ecInstance:[],
            ecUpdate:[],
            IntervalIdStateMachine:[],
            IntervalIdEc2:[],
            lastUpdate:"",
        }
    },
    components: {
        Ec2Status,
        Status
    },

    methods: {
        async ChangePanel($event) {

            if($event.srcElement.outerText == "State Machines") {
                this.MainPanelStateMachine = true;
                this.Ec2Panel = false
            }else {
                this.MainPanelStateMachine = false
                this.Ec2Panel=true
            }
            return this.MainPanelStateMachine
        },

        async RecursiveStateMachineApi() {
            try{
                var response = await axios.get('http://127.0.0.1:8000/api/listStateMachines')
                this.stateMachines = response.data['Aws']
                this.lastUpdate = response.data['UltimaAtt']
                this.Loaded = true;
            }catch(e) {
                console.log(e)
            }
        },

        async RecursiveApicallEc2Instances() {
            try{
                var response = await axios.get('http://127.0.0.1:8000/api/getEc2Instances')
                this.ecInstance = response.data['AWS-EC2']
                this.ecUpdate = response.data['UltimoAtt']
            }catch(e) {
                console.log(e)
            }
        }
        
    },

    async mounted() {
        try{
            this.RecursiveStateMachineApi()
            this.RecursiveApicallEc2Instances()

            setInterval(async () => {
                await this.RecursiveStateMachineApi()
            }, 5000)

            setInterval(async () => {
                await this.RecursiveApicallEc2Instances()
            }, 5000)

        }catch(e) {
            console.error(e)
        }
    },
}

</script>