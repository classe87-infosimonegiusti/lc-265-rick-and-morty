<template>
    <h1 class="text-center">{{title}}</h1>
</template>

<script>
    export default {
        name: 'AppHeader',
        props: {
            title: String
        }
    }
</script>

<style scoped lang="scss">
    @use '../styles/partials/appheader' as *;

</style>