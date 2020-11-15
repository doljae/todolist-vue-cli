<template>
    <div class="taskBoard">
        <section>
            <transition-group name="list" tag="ul">
                <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                    <font-awesome-icon
                        class="checkBtn"
                        icon="check"
                        aria-hidden="true"
                    ></font-awesome-icon>
                    {{ todoItem }}
                    <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
                        <font-awesome-icon icon="trash" aria-hidden="true"></font-awesome-icon>
                    </span>
                </li>
            </transition-group>
        </section>
    </div>
</template>

<script>
export default {
    props: ["propsdata"],
    methods: {
        removeTodo(todoItem, index) {
            console.log("방출");
            this.$emit("removeTodo", todoItem, index);
        },
    },
};
</script>

<style scoped>
ul {
    list-style: none;
}
</style>
