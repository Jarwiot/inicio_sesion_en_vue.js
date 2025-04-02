<script setup>
import { ref } from "vue";
import { auth } from "../firebase";
import { createUserWithEmailAndPassword } from "firebase/auth";
import { useRouter } from "vue-router";

const email = ref("");
const password = ref("");
const router = useRouter();

const register = async () => {
  try {
    await createUserWithEmailAndPassword(auth, email.value, password.value);
    router.push("/dashboard");
  } catch (error) {
    console.error("Error al registrar:", error);
  }
};
</script>

<template>
  <div>
    <h2>Registro</h2>
    <input v-model="email" placeholder="Email" type="email" />
    <input v-model="password" placeholder="Contraseña" type="password" />
    <button @click="register">Registrarse</button>
  </div>
</template>
