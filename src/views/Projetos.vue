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
import { computed } from '@vue/reactivity';
import { defineComponent } from 'vue';
import { useStore } from '@/store';


export default defineComponent({
    name: 'Projetos-Formulario',
    data(){
       return{
        nomeDoProjeto: "",
       }; 
    },
    methods:{
        salvar(){
            this.store.commit('ADICIONA_PROJETO', this.nomeDoProjeto)
            this.nomeDoProjeto = ""; 
        },
        
    },
    setup(){
      const store = useStore()
      return{
        store,
        projetos: computed(() => store.state.projetos)
      }
    }

});

</script>

<style scoped>
.projetos {
    padding: 1.25rem;
}
</style>