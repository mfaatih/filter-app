<template>
  <div id="app">
    <div class="searchs">
      <md-field>
        <label>Ada göre filtre!</label>
        <md-input v-model="type"> </md-input>
      </md-field>
    </div>
    <Cards :posts="posts" :type="type" />
  </div>
</template>

<script>
import axios from 'axios';
import Cards from './components/Cards.vue';

export default {
  components: {
    Cards,
  },

  mounted: function() {
    axios
      .get('https://randomuser.me/api/?results=50')
      .then(response => (this.posts = response.data.results))
      .catch(() => (this.posts = [{name: 'No posts found.'}]))
      .finally(() => console.log('Data loading compilated.'));
  },
  data: function() {
    return {
      posts: [],
      type: '',
    };
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 0;
}
.searchs {
  width: 400px;
  margin: 0px auto;
  text-align: center;
}
</style>
