<script setup>
import headerComponent from '@components/adminHeaderComponent.vue'
import footerComponent from '@components/footerComponent.vue'
import tbComponent from '@/components/tbComponent.vue';

const titles = ['Data', 'Estoque', 'Empréstimos'];
const itens = [
    [
        '01/01/2021',
        '10',
        '5'
    ]
]
</script>
<template>
    <headerComponent activeButton="acervo" />
    <main>
        <RouterLink to="/admin/acervo">Voltar</RouterLink>
        <div>
        <h2>Nome do livro</h2>
        <tbComponent :titles="titles" :itens="itens" :title="'aaaaaaaaaa'" />
        </div>
    </main>
    <footerComponent />
</template>
<style scoped>
main {
    display: flex;
    padding-top: 84px;
    flex-direction: column;
    align-items: center;
}

h2 {
    font-family: 'Inter', sans-serif;
    text-align: left;
    position: relative;
    right: 30px;
}

a {
    font-family: 'Inter', sans-serif;
    text-align: center;
    margin-top: 20px;
}
</style>
<style>
    .list-component-subcomp:hover {
        cursor: pointer;
        background-color: rgba(0, 0, 0, 0.080);
        border-radius: 5px;
    }
</style>