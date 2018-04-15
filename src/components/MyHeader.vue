<template>
    <div class="row">
        <div>
            <h2>Quotes Added</h2>
        </div>
        <div id="divBar">
            <div id="progressBar" :style="currentProgressStyle">{{progressPercent}}/100</div>
        </div>
    </div>
</template>

<script>
    import {eventBus} from "../main.js"

    export default{
        data: function(){
            return {
                progressPercent: 0,
                currentProgressStyle: {
                    width: "0%"
                }
            }
        },
        created(){
            eventBus.$on('quotesLengthHasChanged', (data) => {
                this.progressPercent = data * 10;
                this.currentProgressStyle.width = this.progressPercent + "%";
            });
        }
    }
</script>

<style>
    #divBar{
        width: 80%;
        margin-left: 10%;
        height: 25px;
        border: 1px solid darkgrey;
        border-radius: 5px;
        background-color: lightgray;
    }

    #progressBar{
        height: 23px;
        background-color: royalblue;
        border-radius: 3px;
        color: white;
    }
</style>