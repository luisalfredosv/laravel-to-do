<template>
    <div class="addItem">
        <input type="text" class="input" placeholder="Add todo" v-model="item.name">
        <button class="addBtn" @click="addItem()">
            <font-awesome-icon icon="plus" class="plus" />
        </button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    data(){
        return {
            item: {
                name: ""
            }
        }
    }, 
    methods:{
        addItem(){
            if(this.item.name !== "") {
                axios.post('api/todo/store', {
                    todo: this.item.name
                }).then(resp => {
                    if(resp.status >= 200 && resp.status < 300){
                        this.item.name =null
                    }
                })
            }
        }
    }
}
</script>

<style>
    .addItem {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 25px;
    }

    .input {
        border-style: solid;
        border-color: blue;
        border-bottom-left-radius: 4px;
        border-top-left-radius: 4px;
        border-width: 1px;
        outline: none;
        padding: 5px;
        height: 30px;
        width: 100%;
    }

    .addBtn {
        height: 42px;
        width: 42px;
        border-style: solid;
        border-color: blue;
        border-bottom-right-radius: 4px;
        border-top-right-radius: 4px;
        border-width: 1px;
        background-color: white;
    }

    .plus {
        font-size: 20px;
        color: blue;
    }
</style>