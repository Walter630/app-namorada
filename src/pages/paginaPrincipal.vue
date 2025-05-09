<template>
  <v-main class="principal">
    <h2>Tem certeza</h2>

    <v-menu class="menu" offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="primary" v-bind="props">sim</v-btn>
      </template>

      <v-card width="300px">
        <v-card-text> Se lembra </v-card-text>
        <v-img src="/NossoDia.jpeg" height="300px" cover></v-img>
        <v-btn color="success" @click="mensagem">Sim</v-btn>
      </v-card>
    </v-menu>
    <v-menu class="menu" offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="primary" v-bind="props">sim</v-btn>
      </template>

      <v-card width="300px">
        <v-card-text> e dessa</v-card-text>
        <v-img src="/NossoDia2.jpeg" height="300px" cover></v-img>
        <v-btn color="success" @click="mensagem">Sim</v-btn>
      </v-card>
    </v-menu>
    <v-menu class="menu" offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="primary" v-bind="props">sim</v-btn>
      </template>

      <v-card width="300px">
        <v-card-text> Se lembra dessa tambem </v-card-text>
        <v-img src="/NossoDia3.jpeg" height="300px" cover></v-img>
        <v-btn color="success" @click="mensagem">Sim</v-btn>
      </v-card>
    </v-menu>

    <v-card v-if="msg" class="mt-4" width="300px" align-center>
      <v-card-text>{{ msg }}</v-card-text>
      <v-btn color="error" @click="limpar">apagar</v-btn>
    </v-card>
  </v-main>
  <v-card text-lg-center text-xs-center>
    <v-card-text> Cada uma dessas fotos representa um momento nosso </v-card-text>
  </v-card>

  <v-carousel>
    <v-carousel-item src="/NossoDia4.jpeg"></v-carousel-item>
    <v-carousel-item src="/NossoDia5.jpeg"></v-carousel-item>
    <v-carousel-item src="/NossoDia6.jpeg"></v-carousel-item>
    <v-carousel-item src="/NossoDia7.jpeg"></v-carousel-item>
    <v-carousel-item src="/NossoDia8.jpeg"></v-carousel-item>
    <v-carousel-item src="/NossoDia10.jpeg"></v-carousel-item>
  </v-carousel>
  <div class="heart"></div>
  <v-btn color="error" @click="sair">Sair</v-btn>
</template>

<script>
import { useRouter } from "vuetify/lib/composables/router.mjs";
import { ref } from "vue";
export default {
  setup() {
    const msg = ref("");
    const router = useRouter();
    const mensagem = () => {
      msg.value =
        "Lembro com carinho do dia em que te conheci. Não houve fogos nem trilha sonora, mas havia algo no seu sorriso que me prendeu ali, como se o tempo tivesse decidido parar só para aquele momento. Foi um encontro simples, mas cheio de significado — como se o universo sussurrasse baixinho: “é essa pessoa”. Desde então, minha vida ganhou cor, e cada detalhe ficou mais bonito com você por perto.";
    };
    const limpar = () => {
      msg.value = "";
    };

    const sair = () => {
      router.push("/");
    };
    return {
      mensagem,
      msg,
      limpar,
      sair,
    };
  },
};
</script>

<style>
.principal {
  display: flex;
  justify-content: center;

  margin-top: 1rem;
  padding: 10px;
}

.heart {
  width: 100px;
  height: 90px;
  position: relative;
  background-color: red;
  transform: rotate(-45deg);
  animation: heartbeat 1s infinite;
  margin: 50px auto;
}

.heart::before,
.heart::after {
  content: "";
  width: 100px;
  height: 90px;
  position: absolute;
  background-color: red;
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

@keyframes heartbeat {
  0%,
  100% {
    transform: rotate(-45deg) scale(1);
  }
  25% {
    transform: rotate(-45deg) scale(1.1);
  }
  50% {
    transform: rotate(-45deg) scale(1);
  }
  75% {
    transform: rotate(-45deg) scale(1.1);
  }
}
</style>
