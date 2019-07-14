<template>
  <div id="app">
    <h1>GIF Searcher</h1>
    <Search @SearchRequested="handleSearch"></Search>
    <p v-if="isLoading">Loading...</p>
    <Preview :gifs="gifs" :clearLoaded="isLoading"></Preview>
  </div>
</template>

<script>
import Search from './components/Search'
import Preview from './components/Preview'

export default {
  name: 'app',
  data() {
    return {
      isLoading: true,
      gifs: [],
    }
  },
  components: {
    Search,
    Preview
  },
  methods: {
    doQuery(url) {
      this.isLoading = true;
      fetch(url)
              .then((res) => { return res.json() } )
              .then((res) => {
                this.gifs = res.data;
                this.isLoading = false;
              } )
    },
    handleSearch(query) {
      this.gifs = [];
      this.isLoading = true;
      const url = `https://api.giphy.com/v1/gifs/search?api_key=7QdTbYA7k72XbArWh6RlbjNa0W8oFa7L&q=${query}&limit=25&offset=0&rating=G&lang=en`;
      this.doQuery(url);
    }
  },
  created() {
    const url = `https://api.giphy.com/v1/gifs/trending?api_key=7QdTbYA7k72XbArWh6RlbjNa0W8oFa7L&limit=25&rating=G`;
    this.doQuery(url);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
h1 {
  text-align: center;
}
p {
  text-align: center;
  font-weight: bold;
  font-size: 24px;
}
</style>
