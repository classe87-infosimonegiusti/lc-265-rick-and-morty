<template>
    <div class="character text-center">
        <img class='img-fluid rounded-circle' :src="image" :alt="`Immagine di: ${name}`"/>
        <h3>{{ name }}</h3>
        <h5>{{ species }}</h5>
        <h5>{{ status }}</h5>
    </div>
</template>

<script>
    export default {
        name: 'CharacterCard',
        props: {
            image: String,
            name: String,
            species: String,
            status: String,
        }
    }
</script>


<style>

</style>