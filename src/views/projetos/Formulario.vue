<template>
    <section>
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
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { useStore } from '@/store';
import { ADICIONA_PROJETO, ALTERA_PROJETO, NOTIFICAR } from "@/store/tipo-mutacoes"
import { TipoNotificacao } from '@/interfaces/INotificacao';
import { notificacaoMixion } from '@/mixins/notificar';


export default defineComponent({
    name: 'Projeto-Formulario',
    props: {
        id:{
            type: String
        }
    },
    mixins: [notificacaoMixion],
    mounted() {
        if(this.id){
            const projeto = this.store.state.projetos.find(proj => proj.id == this.id)
            this.nomeDoProjeto = projeto?.nome || ''
        }
    },
    data(){
       return{
        nomeDoProjeto: "",
       }; 
    },
    methods:{
        salvar(){
            if(this.id){
                this.store.commit(ALTERA_PROJETO, {
                    id: this.id,
                    nome: this.nomeDoProjeto
                })
            }else{
                this.store.commit(ADICIONA_PROJETO, this.nomeDoProjeto)
            }
            this.nomeDoProjeto = "";
            this.notificar(TipoNotificacao.SUCESSO, 'Excelente!', 'O projeto foi cadastrado com sucesso')
            this.$router.push('/projetos')
        },
        notificar(tipo: TipoNotificacao, titulo: string, texto: string) {
        this.store.commit(NOTIFICAR, {
            titulo,
            texto,
            tipo
        })
     }
    },
    setup(){
      const store = useStore()
      return{
        store
      }
    }
});
</script>
