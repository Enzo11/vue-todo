<template>
    <form @submit.prevent="addToDo()" class="col-12 col-lg-6">
        <input v-model="newTodo" placeholder="Enter new Todo to the list" type="text" class="form-control">
    </form>
</template>

<script>
export default {
    data(){
        return{
            newTodo: ""
        }
    },
    methods: {
        addToDo(){
            if(this.newTodo.length > 1) {
                this.$emit("on-addtodo", this.newTodo);
            }
            this.newTodo = "";
        }
    }
};
</script>

<style scoped>

</style>
