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
    <header>
        <nav class="navbar navbar-expand-lg bg-dark">
            <div class="container-fluid">

                <a @click="window.location.reload()" class="navbar-brand text-danger fw-bold text-uppercase"
                    href="">Boolflix</a>

                <div class="d-flex col-lg-4 col-md-6 col-sm-6" role="search">
                    <input v-model="store.searchedMovie" @keyup.enter="$emit('searchPerformed')"
                        class="form-control btn-outline-danger me-2" type="search"
                        placeholder="Search Movies or TV Series..." aria-label="Search">
                    <button @click="$emit('searchPerformed')" class="btn btn-outline-danger"
                        type="submit">Search</button>
                </div>

            </div>
        </nav>
    </header>
</template>
<style scoped lang="scss">
@use '../src/style/generic.scss' as *;

header {
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 99;
    box-shadow: 1px 1px 5px 0px #ffffff40;

    nav {
        min-height: 70px;

        .navbar-brand {
            text-shadow: 1px 1px #ffffff60;
        }

        input {
            width: 100%;
        }
    }

}
</style>