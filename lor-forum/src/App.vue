
<template>
  <h1>{{ message }}</h1>
  <h3>List of LOR characters</h3>
  <ul>
    <li v-for="(character, index) in characterList" :key="`character-${index}`">
      <p>{{ character.name }}</p>
      <button @click="addFavorite(character)"> ⭐ favorite</button>
    </li>
  </ul>

  <h3>favotite Characters</h3>
  <ul v-if="favoriteList.length > 0">
    <li v-for="(character, index) in favoriteList" :key="`number-${index}`">⭐{{ character.name }}</li>
  </ul>
  <p v-else> No favorite characters yet</p>

  <br>
  <h3>{{ displayFavoriteLot }}</h3>

  <pre>
        {{ newCharacter }}
      </pre>

  <h3>New character</h3>
  <label for="new-character">new character name: </label>
  <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter">
</template>

<script>
export default {
  data: () => ({
    message: 'Wellcome to Vue',
    characterList: [
      { name: 'Frodo', race: 'Hobbit' },
      { name: 'Sam', race: 'Hobbit' },
      { name: 'Gandalf', race: 'Wizzard' },
      { name: 'Aragorn', race: 'Man' },
      { name: 'Gimly', race: 'Dwarf' },
      { name: 'Legolas', race: 'Elf' },
      { name: 'Merry', race: 'Hobbit' },
      { name: 'Pippin', race: 'Hobbit' },

    ],
    newCharacter: {
      name: ''
    },
    favoriteList: []
  }),
  computed: {
    displayFavoriteLot() {
      if (this.favoriteList.length > 3) {
        return "LOVE TO LOR ♥️"
      } else if (this.favoriteList.length > 0) {
        return "some favorite"
      }
    }
  },
  methods: {
    addFavorite(character) {
      this.favoriteList.push(character)
    },
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: '' }
    }
  },
  watch: {
    favoriteList: {
      handler(newValue, oldValue) {
        console.log(newValue)
      },
      deep: true
    }
  }
}
</script>
