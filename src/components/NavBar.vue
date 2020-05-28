<template>
  <div class="navbar">
    <h1>Search</h1>
    <div class="search">
      <input type="text" v-model="search" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
  props: ['searchParams'],
  data() {
    return {
      search: '',
    }
  },
  methods: {},
}
</script>
