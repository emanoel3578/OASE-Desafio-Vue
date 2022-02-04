<template>
  <div class="flex flex-col h-screen bg-gray-800">

    <div v-if="Loaded">
      <!-- Navbar component -->
      <div>
        <MainMenu />
      </div>

      <!-- Main Panel -->
      <div class="h-full">
        <MainPanel />
      </div>
    </div>

    <div v-else>
      <Loader />
    </div>
  </div>
</template>

<script>
import MainMenu from './components/Header/MainMenu.vue';
import MainPanel from './components/MainContent/MainPanel.vue';
import Loader from './components/Loader/LoaderComponent.vue';

export default {
  
  name:'App',
  data() {
    return {
      Loaded:true,
    }
  },
  components: {
    MainMenu,
    MainPanel,
    Loader,
  },
  
}
</script>
