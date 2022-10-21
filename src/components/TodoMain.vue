<template>
    <div class="medium-size">
        <div class="input-group mb-3">
            <input :value="newTodo" @input="onTodoInput" type="text" class="form-control" placeholder="Escribe un quehacer" aria-label="Escribe un quehacer" aria-describedby="basic-addon2">
            <div class="input-group-append">
                <button @click="onTodoAdd" class="btn btn-outline-secondary" type="button">Añadir</button>
            </div>
        </div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Descripción</th>
                    <th scope="col">Borrar</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(todo, index) in todos" :key="index">
                    <td>{{ index+1 }}</td>
                    <td>{{ todo }}</td>
                    <td>
                        <svg @click="onDeleteRow" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
                            <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
                            <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
                        </svg>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'TodoMain',
    data () {
        return {
            newTodo: "",
            todos: []
        }
    },
    methods: {
        onTodoInput(e) {
            this.newTodo = e.target.value;
        },
        onTodoAdd() {
            console.log('boton');
            this.todos.push(this.newTodo);
            this.newTodo = "";
            localStorage.setItem(sessionStorage.getItem('username'), JSON.stringify(this.todos));
        },
        onDeleteRow(e) {
            const rowToDelete = e.target.parentElement.parentElement.children[0].innerText;
            this.todos.splice(rowToDelete-1,1);
            localStorage.setItem(sessionStorage.getItem('username'), JSON.stringify(this.todos));
        }
    },
    created() {
        const username = sessionStorage.getItem('username');
        this.todos = JSON.parse(localStorage.getItem(username))
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .medium-size {
        margin-left: 25%;
        width: 50%;
    }
</style>
