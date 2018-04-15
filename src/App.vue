<template>
    <div class="container">
        <my-header></my-header><br/>
        <my-body></my-body>
        <my-footer></my-footer>
    </div>
</template>

<script>
    import Footer from './components/MyFooter.vue'
    import Header from './components/MyHeader.vue'
    import Body from './components/MyBody.vue'

    export default {
        components: {
            'my-footer': Footer,
            'my-header': Header,
            'my-body': Body
        }
    }
</script>

<style>
</style>
