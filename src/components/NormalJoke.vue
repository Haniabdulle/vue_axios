<template>
  <div>
    <button @click="send_changed">Normal Joke</button>
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
      this.$root.$emit(`changed_joke`, this.joke);
    },
  },
  data() {
    return {
      joke: undefined,
    };
  }
};
</script>

<style scoped>
button {
  padding: 5px;
}
</style>