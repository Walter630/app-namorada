<template>
  <v-main class="body">
    <h2 style="color: black">Tem certeza</h2>

    <v-menu class="menu" offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="black" v-bind="props">sim</v-btn>
      </template>

      <v-card width="300px">
        <v-card-text> Se lembra </v-card-text>
        <v-img src="/NossoDia.jpeg" height="300px" cover></v-img>
        <v-btn color="success" @click="mensagem">Sim</v-btn>
      </v-card>
    </v-menu>
    <v-menu class="menu" offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="black" v-bind="props">sim</v-btn>
      </template>

      <v-card width="300px">
        <v-card-text> e dessa</v-card-text>
        <v-img src="/NossoDia2.jpeg" height="300px" cover></v-img>
        <v-btn color="success" @click="mensagem2">Sim</v-btn>
      </v-card>
    </v-menu>
    <v-menu class="menu" offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="black" v-bind="props">sim</v-btn>
      </template>

      <v-card width="300px">
        <v-card-text> Se lembra dessa tambem </v-card-text>
        <v-img src="/NossoDia3.jpeg" height="300px" cover></v-img>
        <v-btn color="success" @click="mensagem3">Sim</v-btn>
      </v-card>
    </v-menu>
    <v-container class="text-center">
      <v-card v-if="msg" class="mt-4 mx-auto" max-width="90%">
        <v-card-text class="text-center">{{ msg }}</v-card-text>
        <v-btn color="error" @click="limpar">apagar</v-btn>
      </v-card>
    </v-container>
    <v-container class="text-center">
      <v-card v-if="msg2" class="mt-4 mx-auto" max-width="90%">
        <v-card-text class="text-center">{{ msg2 }}</v-card-text>
        <v-btn color="error" @click="limpar">apagar</v-btn>
      </v-card>
    </v-container>
    <v-container class="text-center">
      <v-card v-if="msg3" class="mt-4 mx-auto" max-width="90%">
        <v-card-text class="text-center">{{ msg3 }}</v-card-text>
        <v-btn color="error" @click="limpar">apagar</v-btn>
      </v-card>
    </v-container>
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
  <div class="heart-fall">
    <span
      v-for="(c, index) in coracoes"
      :key="index"
      class="heart-fall"
      :style="{
        left: c.left + '%',
        animationDuration: c.duration + 's',
        top: '-' + c.size + 'px',
        fontSize: c.size + 'px',
      }"
    >
      ❤️
    </span>
  </div>
</template>

<script>
import { useRouter } from "vuetify/lib/composables/router.mjs";
import { ref } from "vue";
export default {
  setup() {
    const msg = ref("");
    const msg2 = ref("");
    const msg3 = ref("");
    const router = useRouter();
    const mensagem = async () => {
      const texto =
        "Lembro com carinho do dia em que te conheci. Não houve fogos nem trilha sonora, mas havia algo no seu sorriso que me prendeu ali, como se o tempo tivesse decidido parar só para aquele momento. Foi um encontro simples, mas cheio de significado — como se o universo sussurrasse baixinho: “é essa pessoa”. Desde então, minha vida ganhou cor, e cada detalhe ficou mais bonito com você por perto.";
      msg.value = "";
      for (let i = 0; i < texto.length; i++) {
        msg.value += texto[i];
        await new Promise((r) => setTimeout(r, 30));
      }
    };
    const mensagem2 = async () => {
      const texto =
        "Cinco meses, cinco capítulos de uma história que só fica mais bonita. Que sorte a minha ter encontrado em você o meu lar, meu abraço favorito e a paz que eu nem sabia que precisava. Que venham muitos outros meses assim, juntinhos. 💕";
      msg2.value = "";
      for (let i = 0; i < texto.length; i++) {
        msg2.value += texto[i];
        await new Promise((r) => setTimeout(r, 30));
      }
    };
    const mensagem3 = async () => {
      const texto =
        "Hoje completamos 5 meses juntos, e cada dia ao seu lado tem sido uma descoberta linda. Obrigado por transformar minha vida com seu amor, sua paciência e esse sorriso que me desarma. Te amo mais a cada dia. 💖";
      msg3.value = "";
      for (let i = 0; i < texto.length; i++) {
        msg3.value += texto[i];
        await new Promise((r) => setTimeout(r, 30));
      }
    };
    const limpar = () => {
      msg.value = "";
      msg2.value = "";
      msg3.value = "";
    };

    const sair = () => {
      router.push("/");
    };

    const coracoes = ref([]);

    onMounted(() => {
      for (let i = 0; i < 30; i++) {
        coracoes.value.push({
          left: Math.random() * 100,
          duration: 4 + Math.random() * 3,
          size: 16 + Math.random() * 20, // fonte entre 16–36px
        });
      }
    });
    return {
      mensagem,
      mensagem2,
      mensagem3,
      msg,
      msg2,
      msg3,
      limpar,
      sair,
      coracoes,
    };
  },
};
</script>

<style>
.body {
  background: linear-gradient(135deg, #ff7e5f, #feb47b);
  font-family: "Helvetica Neue", sans-serif;
  align-items: center;
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

.coraçoes {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
  z-index: 1;
}

.heart-fall {
  position: absolute;
  animation-name: fall;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

@keyframes fall {
  0% {
    transform: translateY(-100px) rotate(0deg);
    opacity: 1;
  }
  100% {
    transform: translateY(100vh) rotate(360deg);
    opacity: 0;
  }
}

.v-btn {
  margin: 10px;
  padding: 10px;
  width: 20px;
  transition: transform 0.3s ease-in-out;
}
.v-btn:hover {
  transform: scale(1.1);
}
</style>
