<template>
    <div id="app" class="main">
        <todo-header></todo-header>
        <todo-input v-on:addTodo="addTodo"></todo-input>
        <todo-list v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></todo-list>
        <todo-footer v-on:removeAll="clearAll"></todo-footer>
    </div>
</template>

<script>
import TodoFooter from "./components/TodoFooter.vue";
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
    name: "App",
    data() {
        return { todoItems: [] };
    },
    created() {
        if (localStorage.length > 0) {
            for (let i = 0; i < localStorage.length; i++) {
                if (localStorage.key(i) != "loglevel:webpack-dev-server") {
                    this.todoItems.push(localStorage.key(i));
                }
            }
        }
    },
    methods: {
        addTodo(todoItem) {
            console.log(2);
            localStorage.setItem(todoItem, todoItem);
            this.todoItems.push(todoItem);
        },
        clearAll() {
            localStorage.clear();
            this.todoItems = [];
        },
        removeTodo(todoItem, index) {
            console.log(todoItem, index, 1);
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        },
    },
    components: {
        TodoHeader,
        TodoInput,
        TodoList,
        TodoFooter,
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
html {
    height: 100%;
    background-image: linear-gradient(#ff6161, #ff768c);
    background-repeat: no-repeat;
    font-family: sans-serif;
    color: #0f222d;
    background-size: auto;
}

.main {
    width: 400px;
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin: auto;
}
h1 {
    text-align: center;
    color: #fff;
}
.form {
    background-color: #fff;
    padding: 15px;
}
input[type="text"] {
    width: 310px;
    height: 30px;
    outline: 0;
    border: none;
    font-size: 1.5em;
    background: #fff;
    color: #2f4f4f;
}
button {
    font-size: 1.5em;
    color: #53bdff;
    background-color: #fff;
    outline: 0;
    border: none;
    width: 50px;
}
.tasksBoard {
    background-color: #fff;
    margin-top: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    padding-right: 40px;
    /*display: none;*/
}
ul {
    list-style: none;
}
li {
    border-bottom: 1px solid #53bdff;
    padding-bottom: 15px;
    padding-top: 15px;
    font-size: 1.3em;
    color: #2f4f4f;
}
a {
    float: right;
    text-align: right;
    color: #ff6161;
    font-size: 1.2em;
    cursor: pointer;
}
.delete {
    background-color: #ff6161;
    padding: 0px 3px 0px 3px;
    color: #fff;
    cursor: pointer;
}

@media (max-width: 500px) {
    .main {
        margin: auto;
        width: 100%;
    }
    input[type="text"] {
        width: 80%;
    }
    button {
        width: 10%;
    }
}
</style>
