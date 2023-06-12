
  <template>
    <div class="container">
        <PokemonCard v-for="(monster, index) in pokemon"
        :key="monster.name"
        :id="index + 1"
        :pokemon="monster"
        />
    </div>
    </template>
    
    
    <script setup>
    import {ref, onMounted} from 'vue'
    import PokemonCard from '../components/PokemonCard.vue'
    const pokemon = ref('')
    async function getPokemon() {
        let res = await fetch('https://data.cityofnewyork.us/resource/5ucz-vwe8.json')
    let data = await res.json()
    console.log(data)
    pokemon.value = data
    }
    onMounted(() => {
        getPokemon()
    })
    </script>
    <style scoped>
    .container {
        width: 80vw;
        margin: 30px auto;
        display: flex;
        flex-wrap: wrap;
        flex-direction: row;
        align-items: center;
        justify-content: space-around;
    }
    </style>
    