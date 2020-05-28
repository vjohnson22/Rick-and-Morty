<template>
  <div class="showbox-container">
    <h1>{{ data.name }}</h1>
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
}
</script>
