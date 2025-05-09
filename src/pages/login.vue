<route lang="yaml">
meta:
  layout: login
</route>

<template>
  <v-app-bar></v-app-bar>

  <v-main
    style="margin-top: 30px; align-content: center; margin-left: 20%; border-radius: 60px"
  >
    <div v-if="carregando" class="carregando">
      <div class="heart"></div>
      <br />
      <p style="text-align: center; font-size: 40px">Carregando com amor...</p>
    </div>
    <v-card v-else style="text-align: center; width: 600px; align-items: center">
      <v-card-title primary-title> Responda </v-card-title>
      <v-card-text text-h2> Nome </v-card-text>
      <v-text-field v-model="nome" name="name" label="Nome" id="id"></v-text-field>
      <v-card-text v-model="nomeNamorado" text-h2> Nome Namorado </v-card-text>
      <v-text-field name="name" label="Nome do Namorado" id="id"></v-text-field>
      <v-btn color="success" @click="Verificar">confirma</v-btn>
    </v-card>
  </v-main>
</template>

<script>
import { useRouter } from "vue-router";
import { ref } from "vue";
export default {
  setup() {
    const nome = ref("");
    const nomeNamorado = ref("");
    const carregando = ref(false);
    const router = useRouter();

    const Verificar = () => {
      if (nome.value.toLocaleLowerCase().includes("fernanda luiza")) {
        carregando.value = true;
        console.log("Sucesso");
        alert("Aguarde");

        setTimeout(() => {
          router.push("/paginaPrincipal");
        }, 3000);
      } else {
        alert("Pessoa errada nao e fernanda");
      }
    };

    return {
      Verificar,
      nome,
      nomeNamorado,
      carregando,
    };
  },
};
</script>
<style scoped>
.heart {
  width: 100px;
  height: 90px;
  background: red;
  position: relative;
  margin: auto;
  transform: rotate(-45deg);
  animation: pulse 1s infinite;
}

.heart::before,
.heart::after {
  content: "";
  position: absolute;
  width: 100px;
  height: 90px;
  background: red;
  border-radius: 50%;
}

.heart::before {
  top: -50px;
  left: 0;
}

.heart::after {
  left: 50px;
  top: 0;
}

@keyframes pulse {
  0% {
    transform: scale(1) rotate(-45deg);
  }
  50% {
    transform: scale(1.1) rotate(-45deg);
  }
  100% {
    transform: scale(1) rotate(-45deg);
  }
}
</style>
