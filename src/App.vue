<template>
  <div id="app">
    <div class="main">
      <NavBar></NavBar>
      <div class="main-container">
        <ShowBox v-for="datum in data" :key="datum.id" :data="datum"></ShowBox>
      </div>
    </div>
    <div class="favorites">
      <div class="navbar favorites-header"><h1>Favorites</h1></div>
    </div>
  </div>
</template>

<script>
import NavBar from './components/NavBar'
import './style.css'
import data from './data.json'
import ShowBox from './components/ShowBox'

export default {
  name: 'App',
  components: {
    NavBar,
    ShowBox,
  },
  data() {
    return {
      data: data,
    }
  },
}
console.log(data)
</script>
