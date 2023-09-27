
<template>
  <h1>{{ message }}</h1>
  <h3>List of LOR characters</h3>
  <ul>
    <li v-for="(character, index) in characterList" :key="`character-${index}`">
      <p>{{ character.name }}</p>
      <button @click="addFavorite(character)"> ⭐ favorite</button>
    </li>
  </ul>

  <Favorites v-bind:favoriteList="favoriteList" />

  <pre>
        {{ newCharacter }}
      </pre>

  <h3>New character</h3>
  <label for="new-character">new character name: </label>
  <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter">
</template>

<script>
import Favorites from './components/Favorites.vue'
export default {
  components: {
    Favorites
  },
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
