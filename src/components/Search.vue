<template>
  <form @submit.prevent="handleSearch" class="search">
    <input type="search" v-model="word" placeholder="Enter your word" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      word: '',
      uri: 'https://api.dictionaryapi.dev/api/v2/entries/en/',
      wordResult: [],
      error: false,
    };
  },
  methods: {
    handleSearch() {
      if (this.word.trim()) {
        let endPoint = this.uri + this.word;
        fetch(endPoint)
          .then((res) => res.json())
          .then((data) => {
            if (data.length) {
              this.error = false;
              this.wordResult = data;
              this.$emit('wordResult', this.wordResult);
            } else {
              this.error = true;
            }
            this.$emit('error', this.error);
          })
          .catch((err) => {
            console.log(err.message);
          });
      }
    },
  },
};
</script>

<style>
.search {
  background: #c81c42;
  padding: 4rem 0;
}
.search input {
  width: 80%;
  padding: 0.75rem;
  border: none;
  outline: none;
  border-radius: 10px;
  font-family: inherit;
}
</style>
