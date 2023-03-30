<template>

    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-auto">
                <input type="text" class="form-control" placeholder="Search character" v-model="store.search" >
            </div>
            <div class="col-auto">
                <button @click="$emit('doSearch')" class="btn btn-primary">Search</button>
            </div>
            <div class="col-auto">
                <button @click="doReset" class="btn btn-warning">Reset</button>
            </div>
        </div>
    </div>
</template>

<script>

    import { store } from '../store.js';

    export default {
        name: 'AppSearch',
        data() {
            return {
                store
            }
        },
        methods: {
            doReset() {
                this.store.search = '';
                this.$emit('doSearch');
            }
        }
    }
</script>


<style>

</style>