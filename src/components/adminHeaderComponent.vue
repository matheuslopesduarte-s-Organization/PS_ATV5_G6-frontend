<script setup>
import { RouterLink } from 'vue-router'
import { ref } from 'vue'

const props = defineProps({
    isTransparent: {
        required: false,
        type: Boolean,
        default: false
    },
    activeButton: {
        required: false,
        type: String,
        default: 'home'
    }
})
const background = ref({
    backgroundColor: 'white'
})

if (props.isTransparent) {
    background.value = {
        backgroundColor: 'transparent'
    }
}

document.addEventListener('scroll', () => {
    if (window.scrollY > 0 && !props.isTransparent) {
        background.value = {
            backgroundColor: 'white',
            boxShadow: '0px 0px 10px rgba(0, 0, 0, 0.1)'
        }
    } else if (window.scrollY == 0 && !props.isTransparent) {
        background.value = {
            backgroundColor: 'white'
        }
    }
})
</script>
<template>
    <header :style="background">
        <span class="itens">
            <RouterLink :class="activeButton == 'usuarios' ? 'active link' : 'link'" to="/admin/usuarios">Usuários
            </RouterLink>
            <RouterLink :class="activeButton == 'acervo' ? 'active link' : 'link'" to="/admin/acervo">Acervo</RouterLink>
            <RouterLink :class="activeButton == 'adicionar_livro' ? 'active link' : 'link'" class="link" to="/admin/acervo/adicionar">Adicionar livro</RouterLink>
        </span>
        <span class="itens">
            <RouterLink to="/">Voltar</RouterLink>
            <RouterLink :class="activeButton == 'login' ? 'hide login' : 'login'" to="/login">Login</RouterLink>
            <RouterLink :class="activeButton == 'cadastrar' ? 'hide cadastrar' : 'cadastrar'" to="/cadastro">Cadastrar
            </RouterLink>
        </span>
    </header>
</template>
<style scoped>
header {
    z-index: 1;
    color: white;
    text-align: center;
    padding: 10px;
    position: fixed;
    top: 0;
    width: 100%;
    color: black;
    text-decoration: none;
    font-family: 'Inter', sans-serif;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.link {
    color: black;
    text-decoration: none;
    font-weight: 700;
}

.link:hover {
    text-decoration: underline;
}

.link:active {
    color: #5e8194;
}

.itens {
    display: flex;
    align-items: center;
    gap: 45px;
    margin-left: 15px;
}

.logo {
    user-select: none;
}

.login {
    background-color: #333333;
    padding: 10px 20px;
    border-radius: 25px;
    color: white;
    text-decoration: none;
    font-weight: 700;
}

.login:hover {
    background-color: #424242;
}

.login:active {
    background-color: #5e8194;
}

.cadastrar {
    padding: 10px 20px;
    border-radius: 5px;
    color: black;
    text-decoration: none;
    font-weight: 700;
    margin: 0;
    margin-right: 50px;
}

.cadastrar:hover {
    text-decoration: underline;
}

.cadastrar:active {
    color: #5e8194;
}

.hide {
    display: none;
}

.active {
    color: #5e8194;
}
</style>
