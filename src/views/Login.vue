<template>
    <div>
        <header>
            <div class="header-image">
                
            </div>
            <h1>Page Login</h1>
        </header>
        <div class="main-login">
            <form action="/api/value" class="login-form">
                <div class="login-inner">
                    <label for="idInput">아이디</label>
                    <input type="text" id="idInput">
                </div>
                <div class="login-inner">
                    <label for="passwordInput">비밀번호</label>
                    <input type="password" id="passwordInput">
                </div>
                <button class="btn-click" @click.prevent="doLogin">
                </button> 
            </form>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                id: '',
                password: ''
            }
        },

        computed: {
            loginData() {
                return this.loginSource || [];
            }
        },

        asyncComputed: {
            loginSource() {
                return this.loginAPI() || [];
            }
        },

        methods: {
            loginAPI() {
                const url = '/web/api/'

                return this.$x.http(url, {
                    params: {
                        id: this.id,
                        password: this.password
                    }
                })
            }
        }
    }
</script>