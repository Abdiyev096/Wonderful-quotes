<template>
    <div class="quote-add-block">
        <h3>Quote</h3>
        <textarea v-model="textAreaValue" class="quote-add-area">
        </textarea>
        <button @click="passValue" class="quote-add-btn">Add quote</button>
    </div>
</template>

<script>
import {eventBus} from '../main';

export default {
    data() {
        return {
            textAreaValue: ''
        }
    },

    methods: {
        passValue() {
            if(this.textAreaValue.length > 0) {
                eventBus.$emit('addQuote', this.textAreaValue);
            }
        }
    }
    
}
</script>

<style>
    
    .quote-add-block{
        margin-top: 50px;
    }

    .quote-add-area{
        width: 50%;
        height: 20vh;
        padding: 10px;
        text-align: center;
        font-size: 17px;
        resize: none;
    }

    .quote-add-btn{
        display: block;
        margin: 20px auto;
        background-color: dodgerblue;
        outline: none;
        border: none;
        padding: 8px 15px;
        color: white;
        letter-spacing: 0.3px;
        border-radius: 6px;
        cursor: pointer;
        box-shadow: 1px 2px 5px dimgray;
        transition: all 0.6s;
        font-weight: 700;
    }

    .quote-add-btn:hover{
        background-color: blue;
    }

</style>