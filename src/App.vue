<template>
  <div id="app">
    <b-tabs content-class="mt-3">
    <b-tab title="JSON/JS Mutator" active><p><jsonMutator/></p></b-tab>
    <b-tab title="Second"><p>I'm the second tab</p></b-tab>
  </b-tabs>
  </div>
</template>

<script>
import jsonMutator from './components/jsonMutator.vue';

export default {
  name: 'App',
  components: {
    jsonMutator,
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
