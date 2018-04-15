<template>
    <div class="row" id="quotesGrid">
        <single-quote v-for="(quote, i) in quotes" @click.native="destroyQuote(i)">{{quote}}</single-quote>
    </div>
</template>

<script>
    import Quote from './Quote.vue'
    import {eventBus} from '../../main.js'

    export default {
        components: {
            "single-quote": Quote
        },
        data: function() {
            return {
                quotes: []
            }
        },
        created(){
            eventBus.$on('addNewQuote', (data) => {
                this.quotes.push(data);
            });
        },
        watch: {
            quotes(value){
                eventBus.$emit('quotesLengthHasChanged', value.length);
            }
        },
        methods: {
            destroyQuote(i){
                this.quotes.splice(i, 1)
            }
        }
    }
</script>

<style scoped>
    #quotesGrid{
        margin-top: 5%;
    }
</style>