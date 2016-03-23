<template>
    <ul class="list-group">
        <li class="list-group-item up">{{ msg }}</li>
        <li class="list-group-item" @click="clickFn">Dapibus ac facilisis in</li>
        <li class="list-group-item">{{ $route.path }}</li>
        <li class="list-group-item">Porta ac consectetur ac</li>
        <li class="list-group-item">Vestibulum at eros</li>
    </ul>
</template>

<script>
export default {
    data () {
        return {
            msg: 'Cras justo odio'
        }
    },
    methods: {
        clickFn () {
            console.log($.fn.jquery);
        }
    },
    route: {
        canActivate () {
            var isPass;

            $.ajax({
                url: '/path/to/file',
                type: 'POST',
                dataType: 'json'
            })
            .done(function() {
                return isPass = true;
            })
            .fail(function() {
                return isPass = false;
            })
            .always(function() {
                return isPass = true;
            });

            console.log(isPass);

            return isPass;
        }
    }
}
</script>

<style>
</style>