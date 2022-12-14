<template>
    <div>
        <add></add>
        <!-- <div v-if="list.length">
        <ul>
            <li v-for="(item, index) in list">
            <p>{{ item.title }}</p>
            <button @click="remove(index)">delete</button>
            <button @click="update(index)">
                <span v-if="!item.status">edit</span>
                <span v-else>save</span>
            </button>
            <input type="text" v-if="item.status" v-model="list[index].title">
            </li>   
        </ul>
        </div> -->
        <!-- <button @click="testing"></button> -->
    </div>
</template>



<script>

import Add from '@/components/Add.vue'

export default {    
   
    components: {
        add: Add
    },
    methods: {
        testing() {
            console.log(Add.add());
        }
    }
}

</script>

<style>
</style>