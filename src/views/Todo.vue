<template>
    <div class="todo-main">
            <ul v-if="list.length">
                <li v-for="item in list" :key="item.id">
                    {{item.item}}
                <button v-on:click="removeItem(item.id)">Remove Item</button>
                </li>
            </ul>
            <div v-else>
                Nothing in list!
            </div>
        <form v-on:submit.prevent="addToList">
            <input v-model="inputVal"/>
            <button type="submit">Add item</button>
        </form>
    </div>
</template>

<script>
export default {
    name: 'todo',
    data: function() {
        return {
            list: [
                {
                    id: 1,
                    item: 'Testing'
                }
            ],
            inputVal: ''
        }
    },
    methods: {
        addToList: function() {
            let id; 
            this.list.length ? id = this.list[this.list.length - 1].id + 1 : id = 1;
            let newItem = {id, item: this.inputVal}
            this.list.push(newItem)
            this.inputVal = '';
        },
        removeItem: function(id) {
            let newList = this.list.filter(item => item.id != id)
            this.list = newList;
        }
    }
}
</script>

<style>
body {
    margin: 0;
}
/* .todo-main {
    background-color: red;
} */
</style>