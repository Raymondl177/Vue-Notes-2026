<template>
  <div>
<PokemonCard v-for="(poke, index) in pokemon" :key="poke.name" :pokemon="poke" :id="index + 1" />
  </div>
</template>

<script setup>
import {ref, onMounted} from 'vue'
import PokemonCard from '@/components/PokemonCard.vue'
    const pokemon = ref([0])
    async function getPokemon() {
      try{
        const response = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151&offset=0')
        const data = await response.json()
        pokemon.value = data.results
      } catch (error) {
        console.error('Error fetching Pokémon:', error)
      }
    }
    onMounted(() => {
      getPokemon()
    })
</script>

<style scoped>

</style>

