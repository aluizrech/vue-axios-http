<template>
  <div>
    <table class="table">
      <tr>
        <td style="margin-right: 200px">Sigla</td>
        <td>Nome</td>
      </tr>
      <tbody>
        <tr v-for="(estado, index) in estados" :key="index">
          <td>{{estado.sigla}}</td>
          <td>{{estado.nome}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import EstadoBusiness from "@/business/EstadoBusiness"

export default {
  name: "ListarEstados",

  async mounted() {
    await this.listarEstados();
  },

  data(){
    return {
      estados: [],
    }
  },

  methods: {

    async listarEstados(){
      const estados = await EstadoBusiness.getEstados();
      if(estados) {
        this.estados = estados;
      } else {
        console.log("Erro ao carregar estados...");
      }
    },

  }

}
</script>

<style scoped>

.table {
  margin-left: auto;
  margin-right: auto;
}

</style>