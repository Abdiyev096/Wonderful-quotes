<template>
    <header>
        <h2 class="quote-header">Quotes Added</h2>
        <div class="quote-progress-wrap">
            <div class="quote-progressbar" :style="{width: progress * 10 + '%'}"> {{progress}} / 10 </div>
        </div>
    </header>
</template>

<script>
import {eventBus} from '../main';

export default {

    data() {
        return {
            progress: 0
        }
    },

    created() {
        eventBus.$on('increaseProgress', (length) => {
            this.progress = length;
        }),

        eventBus.$on('decreaseProgress', (length) => {
            this.progress = length;
        })
    }
    
}
</script>

<style>

    header .quote-header{
        font-size: 2.6em;
    }

    header .quote-progress-wrap{
        margin: 0 auto;
        width: 85%;
        height: 30px;
        border-radius: 6px;
        box-shadow: 1px 2px 5px dimgray;
    }

    header .quote-progressbar{
        color: white;
        letter-spacing: 0.7px;
        line-height: 32px;
        width: 70%;
        height: 100%;
        background-color: dodgerblue;
        border-radius: 6px;
        transition: all 0.7s;
    }

</style>