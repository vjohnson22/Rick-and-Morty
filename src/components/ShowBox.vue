<template>
  <div class="showbox-container">
    <h1>{{ data.name }}</h1>
    <div class="pic-container">
      <img :src="data.image.original" class="pic" />
    </div>
    <div class="info-container">
      <h2>Season: {{ data.season }}</h2>
      <h2>Episode: {{ data.number }}</h2>
    </div>
    <div>
      <button @click="clickMoreInfo">More Info</button>
      <button @click="add">Add to Favorites</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ShowBox',
  props: {
    data: {
      type: Object,
    },
  },
  methods: {
    clickMoreInfo() {
      this.$emit('clickMoreInfo', this.data)
    },
    add() {
      this.$emit('add', this.data)
    },
  },
}
</script>
