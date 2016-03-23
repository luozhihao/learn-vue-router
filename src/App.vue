<template lang='jade'>
head-top

div.main
    router-view
</template>

<script>
export default {
    components: {
        HeadTop: require('./components/Header.vue')
    }
}
</script>

<style lang="stylus">
@import '../src/assets/css/bootstrap.min.css'

.main 
    width: 100%
</style>