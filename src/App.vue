<template>
  <div id="app">
    <div class="main">
      <div class="navbar">
        <h1>Search</h1>
        <div class="search">
          <input type="text" v-model="search" @input="filter" />
        </div>
      </div>
      <div v-if="episodes.length" class="main-container">
        <ShowBox
          v-for="episode in episodes"
          :key="episode.id"
          :data="episode"
        ></ShowBox>
      </div>
    </div>
    <div class="favorites">
      <div class="navbar favorites-header"><h1>Favorites</h1></div>
    </div>
  </div>
</template>

<script>
import './style.css'
import data from './data.json'
import ShowBox from './components/ShowBox'

export default {
  name: 'App',
  components: {
    ShowBox,
  },
  data() {
    return {
      episodes: data,
      search: '',
    }
  },
  methods: {
    filter() {
      const query = new RegExp(this.search)

      const filteredEpisodes = data.filter(episode => {
        return query.test(episode.name)
      })
      this.episodes = filteredEpisodes
    },
  },
}
</script>
