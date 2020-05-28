<template>
  <div id="app">
    <div class="main">
      <div class="navbar">
        <h1>Search</h1>
        <div class="search">
          <input type="text" v-model="search" @input="filter" />
        </div>
      </div>
      <div v-if="moreInfo.length === 0" class="main-container">
        <ShowBox
          v-for="episode in episodes"
          :key="episode.id"
          :data="episode"
          @clickMoreInfo="handleMoreInfo"
          @add="addToFavs"
        ></ShowBox>
      </div>
      <div v-if="moreInfo.length > 0" class="main-container">
        <Detail
          :episode="moreInfo[0]"
          @goBack="removeMoreInfo"
          @add="addToFavs"
        ></Detail>
      </div>
    </div>
    <div class="favorites">
      <div class="navbar favorites-header">
        <h1>Favorites</h1>
      </div>
      <Favorite
        v-for="favorite in favorites"
        :episode="favorite"
        :key="favorite.id"
        @clickMoreInfo="handleMoreInfo"
        @removeFav="removeFromFavs"
      ></Favorite>
    </div>
  </div>
</template>

<script>
import './style.css'
import data from './data.json'
import ShowBox from './components/ShowBox'
import Detail from './components/Detail'
import Favorite from './components/Favorite'

export default {
  name: 'App',
  components: {
    ShowBox,
    Detail,
    Favorite,
  },
  data() {
    return {
      episodes: data,
      search: '',
      moreInfo: [],
      favorites: [],
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
    handleMoreInfo(episode) {
      if (this.moreInfo.length > 0) {
        this.moreInfo = []
      }
      this.moreInfo.push(episode)
    },
    removeMoreInfo() {
      this.moreInfo = []
    },
    addToFavs(episode) {
      const alreadyFav = this.favorites.filter(fav => {
        return fav.name === episode.name
      })

      if (alreadyFav.length === 0) {
        this.favorites.push(episode)
      }
    },
    removeFromFavs(episode) {
      const favs = this.favorites.filter(fav => {
        return fav.name !== episode.name
      })

      this.favorites = favs
    },
  },
}
</script>
