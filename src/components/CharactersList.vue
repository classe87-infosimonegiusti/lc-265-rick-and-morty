<template>
    <div class="container">
        <div class="row">
            <div class="col-3" v-for="(character, index) in store.charactersList" :key="index">
                <CharacterCard  
                    :image="character.image"
                    :name="character.name"
                    :species="character.species"
                    :status="character.status"
                />
            </div>
        </div>
    </div>
</template>


<script>

    import {store} from '../store.js';
    import CharacterCard from './CharacterCard.vue';

    export default {
        name: 'CharactersList',
        data() {
            return {
                store
            }
        },
        components: {
            CharacterCard
        }
    }
</script>


<style>

</style>