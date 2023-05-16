<template>
    <section class="projetos"></section>
    <h1>Projetos</h1>
    <form @submit.prevent="salvar">
        <div class="field">
            <label for="nomeDoProjeto" class="label">
                Nome do Projeto
            </label>
            <input 
            type="text" 
            class="input"
            v-model="nomeDoProjeto"
            id="nomeDoProjet"
            />
        </div>
        <div class="field">
            <button class="button" type="submit">Salvar</button>
        </div>
    </form>
    <table class="table is-fullwidth">
        <thead>
            <tr>
                <td>ID</td>
                <td>Nome</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="projeto in projetos" :key="projeto.id">
                <th>{{ projeto.id }}</th>
                <th>{{ projeto.nome }}</th>
            </tr>
        </tbody>
    </table>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import IProjeto from '../interfaces/IProjeto'


export default defineComponent({
    name: 'Projetos-Formulario',
    data(){
       return{
        nomeDoProjeto: "",
        projetos: [] as IProjeto[]
       } 
    },
    methods:{
        salvar(){
            const projeto: IProjeto = {
                nome: this.nomeDoProjeto,
                id: new Date().toISOString()
            }
            this.projetos.push(projeto)
            this.nomeDoProjeto = ''
            
        }
        
    }
})

</script>

<style scoped>
.projetos {
    padding: 1.25rem;
}
</style>