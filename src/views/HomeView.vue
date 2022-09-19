<template>
  <div>
    <h1 id="titulo">Home - Título Principal</h1>
    <h2 :style="{ color: cor.atual }">Home - Título Secundário</h2>
    <div v-show="cor.atual === 'blue'">A cor é: azul</div>

    <input type="text" v-model="cor.atual" @keydown="mudaCor()" /><br />
    <button @click="mudaCor()">Muda cor do Título</button>
    <p v-html="cor.atual" />

    <div v-if="cor.atual === 'red'">vermelho</div>
    <div v-else>Agora não é vermelho agora é: {{ cor.atual }}</div>

    <div v-show="cor.atual === 'cores'">
      <h3>Tabela de Cores</h3>

      <table>
        <thead>
          <tr>
            <th>Nome da Cor</th>
            <th>Código da Cor</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(cor, index) in cores" :key="index">
            <td>{{ cor.nome }}</td>
            <td>{{ cor.id }}</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div v-html="texto.html"></div>

    <!-- Não entendi muito bem como usar -->
    <span v-pre>{{ this will not be compiled }}</span>

    <!-- Renderize o elemento e o componente apenas uma vez e ignore as atualizações futuras. -->
    <div v-once>
      <input type="text" v-model="cor.atual" @keydown="mudaCor()" /><br />
    </div>
  </div>

  <!-- Não entendi muito bem como usar -->
  <div v-memo="[valueA, valueB]">...</div>
</template>

<script>
export default {
  name: "HomeView",
  data() {
    return {
      cor: {
        atual: "",
      },
      cores: [
        { nome: "red", id: "#FF0000" },
        { nome: "blue", id: "#0000FF" },
        { nome: "black", id: "#000000" },
        { nome: "orange", id: "#FFA500" },
      ],
      texto: {
        html: "<div><h2>Testando o v-html...</h2></div>",
        // script:
      },
    };
  },
  methods: {
    mudaCor() {
      document.getElementById("titulo").style.color = this.cor.atual;
    },
  },
};
</script>
