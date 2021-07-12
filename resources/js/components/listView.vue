<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item
            :item="item"
            class="item"
            />
        </div>
    </div>
</template>

<script>
import listItem from './listitem'
import Listitem from './listitem.vue'
export default {
    components: {
        listItem
    },
    data: function() {
        return {
            items : []
        }
    },
    methods: {
        getTodos() {
            axios.get('api/todos').then(response => {
                if(response.status === 200) {
                    this.items = response.data.todos
                }
            })
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
        border-style: blue;
        border-radius: 7px;
        border-width: 1px;
    }
</style>