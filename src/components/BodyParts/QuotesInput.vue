<template>
    <div class="container">
        <div class="row">
            <div class="col-lg-4 col-lg-offset-4">
                <h3>Quote</h3>
                <textarea v-model="quote"></textarea><br/>
                <div class="col-sm-12" align="center">
                    <button id="addBtn" @click="addQuote">Add Quote</button>
                </div>
            </div>
            </div>
        </div>
</template>

<script>
import {eventBus} from '../../main.js'

    export default {
        data: function(){
           return {
               quote: '',
               isQuotesGridFull: false
           }
        },
        methods: {
            addQuote(){
                if(this.quote === ''){
                    alert("You must enter quote !");
                }
                else if(this.isQuotesGridFull){
                    alert("The quotes grid is full! Delete something.");
                }
                else{
                    eventBus.$emit('addNewQuote', this.quote);
                    this.quote = '';
                }
            }
        },
        created(){
            eventBus.$on('quotesLengthHasChanged', (data) => {
                if(data === 10){
                    this.isQuotesGridFull = true;
                }
                else{
                    this.isQuotesGridFull = false;
                }
            });
        }
    }
</script>

<style scoped>
    #addBtn{
        background-color: royalblue;
        color:white;
    }
    textarea{
        width: 100%;
        height: 100px;
    }

</style>