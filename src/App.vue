<template>
  <div id="app">
    <home-page/>
    <!-- <li v-for="item in arrayPokemons" :key="item.key">
      {{ item.name }} {{ 
      }}
    </li> -->
    
  </div>
</template>

<script>
import HomePage from './HomePage.vue';
import events from './services/events';

export default {
  components: { HomePage },
  data(){
    return {
      arrayPokemons: []
    }
  },

  mounted(){
    events.list().then(resposta => {
      this.arrayPokemons = resposta.data.results
      console.log("consultando:", resposta.data.results)
    })
  }

}
</script>

<style scoped>

#app {
  background-color: #808080;
}

</style>
