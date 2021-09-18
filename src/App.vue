<template>
  <Search @wordResult="results = $event" @error="showError = $event" />

  <div v-if="showError">
    <NotFound />
  </div>
  <div v-else>
    <Result :results="results" />
  </div>
</template>

<script>
import Result from './components/Result.vue';
import Search from './components/Search.vue';
import NotFound from './components/NotFound.vue';

export default {
  name: 'App',
  data: () => {
    return {
      results: [],
      showError: false,
    };
  },
  components: {
    Search,
    Result,
    NotFound,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  background: #faf0e8;
}
ul,
li {
  list-style: none;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #faf0e8;
  min-height: 100vh;
  height: 100%;
}
</style>
