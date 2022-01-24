<template>
    <h1 v-if="!pokemon">Espere por favor ...</h1>
    <div v-else>
        <h1>¿Quién es este Pokemón?</h1>
        <Pokemon-Picture :pokeId="pokemon.id" :showPokemon="showPokemon"/>
        <Pokemon-Options :pokemons="pokemonsArr" @selection-pokemon="checkPokemon"/>
    </div>
</template>

<script>
import PokemonPicture from '@/components/PokemonPicture.vue'
import PokemonOptions from '@/components/PokemonOptions.vue'
import getPokemonOptions from '@/helpers/getPokemonOptions'

export default {
    name: 'Pokemon-Page',
    components: {
        PokemonPicture, PokemonOptions
    },
    data(){
        return{
            pokemonsArr:[],
            pokemon: null,
            showPokemon:false
        }
    },
    methods:{
        async mixGetPokemons(){
            this.pokemonsArr = await getPokemonOptions()

            let rndInt = Math.floor( Math.random() * 4)

            this.pokemon = this.pokemonsArr[rndInt]
        },
        checkPokemon( PokemonId ){
            (PokemonId === this.pokemon.id) ? this.showPokemon = true : this.showPokemon = false
        }
    },
    
    mounted(){
        this.mixGetPokemons()
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
*{
    font-family: 'Poppins',Arial, Helvetica, sans-serif;
}
</style>