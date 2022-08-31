<template>
  <div id="app">
 <joke-button></joke-button>
    <div class="paragraph">
      <div v-if="joke !== undefined">
      <p>{{joke}}</p>
      </div>
  <div v-else-if ="joke === undefined">
    </div>
    </div>

  
    <normal-joke></normal-joke>
    <snake-joke></snake-joke>
    <loud-joke></loud-joke>
  </div>
</template>

<script>
import JokeButton from '@/components/JokeButton.vue';
import SnakeJoke from "@/components/SnakeJoke.vue";
import NormalJoke from '@/components/NormalJoke.vue';
import LoudJoke from '@/components/LoudJoke.vue';
export default {
  name: 'App',
  components: {
    JokeButton,
    SnakeJoke,
    NormalJoke,
    LoudJoke
  },
  methods: {
    joke_recieved(random_joke) {
      this.joke = random_joke;
    },
    show_changed(random_joke){
      if(this.joke !== undefined){
        this.joke = random_joke;
      }
    },
  },
  mounted () {
    this.$root.$on(`joke_sent`,this.joke_recieved);
    this.$root.$on(`changed_joke`,this.show_changed);
  },
  data() {
    return {
      joke: undefined,
    }
  },
}
</script>

<style scoped> 
#app{
  text-align: center;
  display: grid;
  gap: 30px;
}

</style>