<template>
    <body>
        <h1>TodoList</h1>
        <tr>
            <p>Title</p>
            <input type="text"  v-model="title" />
            <p>Content</p>
            <textarea type="text" v-model="content" rows="3" cols="50">write something....</textarea>
            <button v-on:click="addTodo()">追加</button>
            <button v-on:click="getTodo()">テスト取得</button>
        </tr>
        

        <table>
            <thead><tr><th>KEY</th><th>TITLE</th><th>TEXT</th></tr></thead>
            <tbody>
            <tr v-for="todo in todos" :key="todo">
                <td> {{todo.id}}</td>
                <td> {{todo.title}}</td>
                <td> {{todo.content}}</td>
                <td>
                <button v-on:click="deleteTodo(todo)">削除</button> 
                </td>
            </tr>
            </tbody>
        </table>
    </body>
</template>

<script>
import axios from 'axios';

export default {
    data: function() {
        return {
            id:'',
            title: '',
            content: '',
            todos: []
        }
    },
    methods: {
        getTodo() {
            const getEndpoint = 'http://localhost:8000/gettodo';
            axios.get(getEndpoint)
            .then((res)=> {
                this.todos = res.data.todos;
            })
        },
        addTodo() {
            const addEndpoint = 'http://localhost:8000/addtodo';
            console.log(addEndpoint)
            const todo = {
                title: this.title,
                content: this.content
            }
            axios.post(addEndpoint, todo)
            .then((res)=> {
                this.todos.push(res.data)
            })
            this.getTodo();//for reload
        },
        deleteTodo(todo) {
            const deleteEndpoint = 'http://localhost:8000/deletetodo';
            console.log(deleteEndpoint)
            console.log(todo)
            
            axios.post(deleteEndpoint, todo)
            .then((res)=> {
                this.todos = res.data.todo;
            })
            this.getTodo();//for reload
        }
    },
    created: function() {
        this.getTodo();
    }
}
</script>