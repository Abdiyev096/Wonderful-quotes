<template>
    <div class="quote-list">
        <QuoteItem 
                v-for="(list, index) in quoteList"
                :key="index"
                :quoteList="list"/>
    </div>
</template>

<script>
import QuoteItem from './Quote-item';
import {eventBus} from '../main';

export default {
    data() {
        return {
            quoteList: []
        }
    },

    created() {
        eventBus.$on('addQuote', (value) => {
            if(this.quoteList.length < 10) {
                const obj = {text: value};
                const newArr = [...this.quoteList, obj];
                this.quoteList = newArr;
                eventBus.$emit('increaseProgress', this.quoteList.length);
            }
        }),

        eventBus.$on('onDelete', (value) => {
            const i = this.quoteList.indexOf(value);
            const arr1 = this.quoteList.slice(0, i);
            const arr2 = this.quoteList.slice(i + 1);
            this.quoteList = [...arr1, ...arr2];
            eventBus.$emit('decreaseProgress', this.quoteList.length);
        })
    },

    components: {
        QuoteItem
    }
}
</script>

<style>

    .quote-list{
        margin: 50px auto;
        padding: 10px 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
    }

</style>


