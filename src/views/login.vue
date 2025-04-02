<script setup>
import { ref } from "vue";
import { auth } from "../firebase";
import { signInWithEmailAndPassword } from "firebase/auth";
import { useRouter } from "vue-router";

const email = ref("");
const password = ref("");
const router = useRouter();

const login = async () => {
  try {
    await signInWithEmailAndPassword(auth, email.value, password.value);
    router.push("/dashboard");
  } catch (error) {
    console.error("Error al iniciar sesión:", error);
  }
};
</script>

<template>
  <div>
    <h2>Iniciar Sesión</h2>
    <input v-model="email" placeholder="Email" type="email" />
    <input v-model="password" placeholder="Contraseña" type="password" />
    <button @click="login">Iniciar Sesión</button>
  </div>
</template>
