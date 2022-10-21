<template>
    <div class="medium-size">
        <div class="input-group mb-3">
            <input :value="username" @input="onUsernameInput" type="text" class="form-control" placeholder="Nombre de usuario" aria-label="Nombre de usuario" aria-describedby="basic-addon2">
            <div class="input-group-append">
                <button @click="onLogin" class="btn btn-outline-secondary" type="button">Login</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoMain',
    data () {
        return {
            username: "",
        }
    },
    methods: {
        onUsernameInput(e) {
            this.username = e.target.value;
        },
        onLogin() {
            this.$emit('user-login');
            sessionStorage.setItem('username', this.username);
        },
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
