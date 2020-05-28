<template>
  <div class="more-info-page">
    <button id="go-back-button" @click="goBack">Go Back</button>
    <button id="go-back-button" @click="add">Add to Favorites</button>
    <div class="more-info-container">
      <h1>{{ episode.name }}</h1>
      <h2>Season: {{ episode.season }}</h2>
      <h2>Episode: {{ episode.number }}</h2>
      <h2>Air date: {{ episode.airdate }}</h2>
      <img :src="episode.image.original" class="info-pic" />
      <h3>Synopsis: {{ episode.summary }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  props: {
    episode: Object,
  },
  methods: {
    goBack() {
      this.$emit('goBack')
    },
    add() {
      this.$emit('add', this.episode)
    },
  },
}
</script>
