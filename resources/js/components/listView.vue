<template>
    <div>
        <div v-for="(item, i) in items" :key="i">
            <list-item
                :item="item"
                class="item"
            />
        </div>
    </div>
</template>

<script>

import axios from 'axios';
import listItem from "./listItem";

export default {
    components:{
        listItem
    },
    data() {
        return {
            items: []
        }
    },
    methods: {
        getTodos() {
            axios.get('api/todos').then( resp => {
                if(resp.status === 200){
                    this.items = resp.data.todos
                }
            });
        }
    },
    created() {
        this.getTodos()
    }
}
</script>

<style>

    .item {
        padding: 12px;
        margin-top: 5px;
        border-style: solid;
        border-color: blue;
        border-radius: 7px;
        border-width: 1px;
    }

</style>