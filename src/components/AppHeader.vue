<script>
export default {
    name: 'AppHeader'
}
</script>

<template>
    <nav class="navbar navbar-expand-lg bg-dark">
        <div class="container-fluid">

            <a class="navbar-brand text-danger fw-bold text-uppercase" href="#">Boolfix</a>

            <div class="d-flex" role="search">
                <input class="form-control btn-outline-danger me-2" type="search" placeholder="Search"
                    aria-label="Search">
                <button class="btn btn-outline-danger" type="submit">Search</button>
            </div>

        </div>
    </nav>
</template>
<style lang="scss">
@use '../src/style/generic.scss' as *;

nav {
    .navbar-brand {
        text-shadow: 1px 1px #ffffff60;
    }
}
</style>