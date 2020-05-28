<template>
  <div class="fav-container">
    <img :src="episode.image.medium" class="fav-pic" />
    <div class="fav-button-container">
      <button @click="clickMoreInfo">More Info</button>
      <button @click="removeFav">Remove from Favorites</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Favorite',
  props: {
    episode: Object,
  },
  methods: {
    clickMoreInfo() {
      this.$emit('clickMoreInfo', this.episode)
    },
    removeFav() {
      this.$emit('removeFav', this.episode)
    },
  },
}
</script>
