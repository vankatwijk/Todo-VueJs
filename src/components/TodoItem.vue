<template>
    <div class='todo-item' v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props:["todo"],
    methods:{
        markComplete(){
           this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo-item{
        background:#f4f4f4;
        padding:10px;
        border-bottom:1px #cc dotted;
    }
    .is-complete{
        text-decoration:line-through
    }
    .del{
        background: #ff0000;
        color:#fff;
        border:none;
        padding:4px 9px;
        border-radius:50%;
        cursor:pointer;
        float:right;
    }
</style>