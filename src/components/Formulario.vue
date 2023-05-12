<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" 
                class="input" 
                placeholder="Qual tarefa você deseja iniciar?"
                v-model="descricao"
                >
            </div>
        <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import Temporizador from './Temporizador.vue';

    export default defineComponent({
    name: "formu-lario",
    emits: ['aoSalvarTarefa'],
    components:{
        Temporizador
    },
    data (){
        return{
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number): void{
            console.log(`Tempo da tarefa ${tempoDecorrido}, tarafa ${this.descricao}`);
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
    }
},
});
</script>