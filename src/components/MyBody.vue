<template>
    <div class="container">
        <div class="row">
            <quotes-input></quotes-input>
            <quotes-log></quotes-log>
        </div>
    </div>
</template>

<script>
    import QuotesInput from './BodyParts/QuotesInput.vue'
    import QuotesLog from './BodyParts/QuotesLog.vue'

    export default{
        components: {
            'quotes-input': QuotesInput,
            'quotes-log': QuotesLog
        }
    }
</script>