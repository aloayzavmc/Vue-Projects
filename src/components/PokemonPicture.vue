<template>
    <div class="pokemon-container">
        <img :src="imgSrc"
        class="poke-hidden"
        alt="Pokemon">
        <img :src="imgSrc" v-if="showPokemon"
        class="fade-in"
        alt="Pokemon">
    </div>
</template>

<script>
export default {    
    name: 'Pokemon-Picture',
    props:{
        pokeId: {
            type: Number,
            required :true
        },
        showPokemon: {
            type: Boolean,
            required: true,
            default: false
        }
    },
    data(){
        
    },
    computed:{
        imgSrc(){
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokeId}.svg`
        }
    }
}
</script>

<style scoped>
/* Pokemon Picture */
.pokemon-container {
    height: 200px;
}

img {
    height: 200px;
    position: absolute;
    width: 100vw;
    margin-left: -50vw;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}


.poke-hidden{
    filter: brightness(0);
}
</style>