<script setup>
import { auth } from "../firebase";
import { signOut } from "firebase/auth";
import { useRouter } from "vue-router";

const router = useRouter();

const logout = async () => {
  await signOut(auth);
  router.push("/login");
};
</script>

<template>
  <div>
    <h2>Dashboard</h2>
    <button @click="logout">Cerrar Sesión</button>
  </div>
</template>
