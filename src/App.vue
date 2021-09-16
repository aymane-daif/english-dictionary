<template>
  <Search @wordResult="results = $event" />
  <Result :results="results" />
</template>

<script>
import Result from './components/Result.vue';
import Search from './components/Search.vue';

export default {
  name: 'App',
  methods: {},
  data() {
    return {
      results: [],
    };
  },
  components: {
    Search,
    Result,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
