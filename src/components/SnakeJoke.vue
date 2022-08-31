<template>
  <div>
    <!-- button will fire the send changed method -->
    <button v-on:click="send_changed">Snake Joke</button>
  </div>
</template>

<script>
export default {
  mounted() {
    this.$root.$on(`joke_sent`, this.convert_joke);
  },
  methods: {
    convert_joke(random_joke) {
      this.joke = random_joke;
    },
    send_changed() {
      this.$root.$emit(`changed_joke`, this.joke.replaceAll(" ","_"));
    },
  },
  data() {
    return {
      joke: undefined
    };
  },
};
</script>

<style scoped>
button {
  padding: 5px;
}
</style>