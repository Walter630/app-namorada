<template>
  <v-app-bar elevation-3>
    <v-app-bar-nav-icon> </v-app-bar-nav-icon>
    <v-app-bar-title>Amor</v-app-bar-title>
  </v-app-bar>
  <v-main class="body">
    <div class="heart" ma-5></div>
    <v-card color="black" dark>
      <v-card-title primary-title> Preparesse Amor </v-card-title>
      <v-btn color="success" @click="Verificar" icon>
        <v-icon>mdi-heart</v-icon> Sim
      </v-btn>
      <v-btn color="error" @click="alerta" icon class="shake">
        <v-icon>mdi-close</v-icon> Não
      </v-btn>
    </v-card>
    <v-card-title> Voce quer uma dica... </v-card-title>
    <v-menu offset-y>
      <template v-slot:activator="{ props }">
        <v-btn color="primary" v-bind="props">Sim</v-btn>
      </template>
      <v-card width="300px">
        <v-card-text> Nosso dia meu amor e vai ter muitos iguais a esse </v-card-text>
        <v-img src="/NossoDia.jpeg" cover></v-img>
      </v-card>
    </v-menu>
  </v-main>
</template>

<script>
import { useRouter } from "vue-router";
export default {
  setup() {
    const router = useRouter();
    const alerta = () => {
      const resposta = confirm("Tem certeza disso");
      if (resposta) {
        alert("Saindo...");
      }
    };
    const Verificar = () => {
      router.push("/login");
    };

    return {
      alerta,
      Verificar,
    };
  },
};
</script>

<style scoped>
.body {
  background: linear-gradient(135deg, #ff7e5f, #feb47b);
  font-family: "Helvetica Neue", sans-serif;
  align-items: center;
}

.heart {
  width: 120px;
  height: 120px;
  position: relative;
  background-color: red;
  transform: rotate(-45deg);
  animation: heartbeat 1s infinite;
  margin: 50px auto;
  box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
}

.heart::before,
.heart::after {
  content: "";
  width: 120px;
  height: 120px;
  position: absolute;
  background-color: red;
  border-radius: 50%;
}

.heart::before {
  top: -60px;
  left: 0;
}

.heart::after {
  left: 60px;
  top: 0;
}

/* Animação de batimento cardíaco */
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
.v-card {
  text-align: center;
  border-radius: 12px;
  padding: 20px;
  margin: 50px;
}
.v-btn {
  margin: 10px;
  padding: 20px;
  transition: transform 0.3s ease-in-out;
}
.v-btn:hover {
  transform: scale(1.1);
}
/* Estilo de texto no card */
.v-card-title {
  font-size: 24px;
  font-weight: bold;
  color: #7c0c0c;
  text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
}

.shake {
  animation: shake 1.2s ease-in-out infinite;
}
@keyframes shake {
  0% {
    transform: translateX(0);
  }
  25% {
    transform: translateY(-100px);
  }
  50% {
    transform: translateX(100px);
  }
  75% {
    transform: translateX(-20px);
  }
  100% {
    transform: translateX(0);
  }
}
</style>
