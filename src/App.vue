<template>
  <div class="flex flex-col h-screen bg-gray-800">

    <div v-show="LoaderOff">
      <!-- Navbar component -->
      <div>
        <MainMenu />
      </div>

      <!-- Main Panel -->
      <div class="h-full">
        <MainPanel/>
      </div>
    </div>

    <div v-show="LoaderOn">
      <Loader  />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import MainMenu from './components/Header/MainMenu.vue';
import MainPanel from './components/MainContent/MainPanel.vue';
import Loader from './components/Loader/LoaderComponent.vue';

export default {
  
  name:'App',
  data() {
    return {
      LoaderOn:true,
      LoaderOff:false,
      stateMachines: [],
    }
  },
  components: {
    MainMenu,
    MainPanel,
    Loader,
  },

  async mounted() {
    try{
      await axios.get('http://127.0.0.1:8000/api/listStateMachines')
      setTimeout(()=> {this.LoaderOn = false,this.LoaderOff=true}, 1000)
    }catch(e) {
        console.log(e)
    }
  }

}
</script>
