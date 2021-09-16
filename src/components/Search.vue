<template>
  <form @submit.prevent="handleSearch">
    <input type="search" v-model="word" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      word: '',
      uri: 'https://api.dictionaryapi.dev/api/v2/entries/en/',
      wordResult: [],
    };
  },
  methods: {
    handleSearch() {
      console.log(this.word);
      if (this.word.trim()) {
        let endPoint = this.uri + this.word;
        fetch(endPoint)
          .then((res) => res.json())
          .then((data) => {
            console.log(data);
            this.wordResult = data[0];
            this.$emit('wordResult', data[0]);
          })

          .catch((err) => {
            console.log(err.message);
          });
      }
    },
  },
};
</script>

<style></style>
