<template>
    <div class="clearAllContainer" v-on:click="clearTodo">
        <span class="clearAllBtn "><h4>clear all</h4></span>
    </div>
</template>

<script>
export default {
    methods: {
        clearTodo() {
            this.$emit("removeAll");
            console.log(1);
        },
    },
};
</script>

<style scoped>
h4 {
    color: white;
    font-weight: 900;
    margin: 2.5rem 0 1.5rem;
}
</style>
