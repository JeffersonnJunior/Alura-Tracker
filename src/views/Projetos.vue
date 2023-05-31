<template>
    <section class="projetos"></section>
    <h1>Projetos</h1>
    <router-link to="/projetos/novo" class="button">
      <span class="icon is-small">
        <i class="fas fa-plus"></i>
      </span>
      <span>Novo projeto</span>
    </router-link>
    <table class="table is-fullwidth">
        <thead>
            <tr>
                <th>Id</th>
                <th>Nome</th>
                <th>
                    Ações
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="projeto in projetos" :key="projeto.id">
                <td>{{ projeto.id }}</td>
                <td>{{ projeto.nome }}</td>
                <td>
                    <router-link :to="`/projetos/${projeto.id}`" class="button">
                    <span class="icon is-small">
                    <i class="fas fa-pencil-alt"></i>
                    </span>
                    </router-link>
                </td>
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
    setup(){
      const store = useStore()
      return{
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