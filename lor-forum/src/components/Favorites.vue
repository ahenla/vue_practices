<template>
  <h3>favotite Characters</h3>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character, index) in favoriteList" :key="`number-${index}`">⭐{{ character.name }}</li>
  </ul>
  <p v-else> No favorite characters yet</p>

  <br>
  <h3>{{ displayFavoriteLot }}</h3>
</template>

<script>
export default {
  props: {
    favoriteList: {
      type: Array,
      required: true
    }
  },
  computed: {
    displayFavoriteLot() {
      if (this.favoriteList.length > 3) {
        return "LOVE TO LOR ♥️"
      } else if (this.favoriteList.length > 0) {
        return "some favorite"
      }
    }
  }
}

</script>
