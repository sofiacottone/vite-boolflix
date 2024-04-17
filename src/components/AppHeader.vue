<script>
import { store } from '../store.js'

export default {
    name: 'AppHeader',
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <nav class="navbar navbar-expand-lg bg-dark">
        <div class="container-fluid">

            <a class="navbar-brand text-danger fw-bold text-uppercase" href="#">Boolflix</a>

            <div class="d-flex" role="search">
                <input v-model="store.searchedMovie" class="form-control btn-outline-danger me-2" type="search"
                    placeholder="Search" aria-label="Search">
                <button @click="$emit('searchPerformed')" class="btn btn-outline-danger" type="submit">Search</button>
            </div>

        </div>
    </nav>
</template>
<style scoped lang="scss">
@use '../src/style/generic.scss' as *;

nav {
    .navbar-brand {
        text-shadow: 1px 1px #ffffff60;
    }
}
</style>