<template>
    <div @click="deleteQuote" class="quote-item" >
        {{quoteList.text}}
    </div>
</template>

<script>
import {eventBus} from '../main';

export default {
    props: ['quoteList'],

    methods: {
        deleteQuote() {
            eventBus.$emit('onDelete', this.quoteList);
        }
    }
}
</script>

<style>

    .quote-item{
        text-align: left;
        padding: 25px 20px;
        border-radius: 15px;
        min-width: 15%;
        max-width: 30%;
        min-height: 4em;
        max-height: 8em;
        margin: 10px 20px;
        border: 1px solid dimgray;
        box-shadow: 1px 2px 5px dimgray;
        overflow: auto;
        cursor: pointer;
    }

</style>