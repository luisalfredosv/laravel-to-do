<template>
    <div>
        <h1 style="margin-top:200px; text-align:center">Todo List</h1>
            <div class="todoListContainter">
                <add-item-form />
                <list-view />
            </div>
    </div>
</template>

<script>

    import addItemForm from "./addItemForm"
    import AddItemForm from './addItemForm.vue'
    import listView from "./listView.vue"

    export default {
        components: {
            addItemForm,
            listView,
                AddItemForm
        }
    }

</script>

<style  scoped>
    .todoListContainter {
        width: 400px;
        margin: auto;
        margin-top: 50px;
    }

</style>