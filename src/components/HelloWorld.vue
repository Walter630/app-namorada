<template>
  <v-app-bar elevation-3>
    <v-app-bar-nav-icon></v-app-bar-nav-icon>
    <v-app-bar-title>Amor</v-app-bar-title>
  </v-app-bar>
  <div class="heart" ma-5 style="margin-top: 80px"></div>
  <v-main>
    <v-card style="text-align: center">
      <v-card-title primary-title> Ta preparada </v-card-title>
      <v-btn color="success" @click="Verificar">Sim</v-btn>
      <v-btn color="error" @click="alerta">Nao</v-btn>
    </v-card>
  </v-main>
</template>

<script>
import { useRouter } from "vue-router";
export default {
  setup() {
    const router = useRouter();
    const alerta = () => {
      alert("Tem q estar");
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

<style>
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
