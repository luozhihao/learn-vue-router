<template>
    <nav class="navbar navbar-default">
        <div class="container-fluid">
            <div class="navbar-header">
                <a class="navbar-brand" v-link="{ path: '/foo' }">Brand</a>
            </div>
            <div class="collapse navbar-collapse">
                <ul class="nav navbar-nav">
                    <li class="active" v-link="{ path: '/foo' }"><a>Foo </a></li>
                    <li v-link="{ path: '/bar' }"><a>Bar</a></li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
</script>

<style scoped>
.nav li:hover{
    cursor: pointer;
}
</style>

