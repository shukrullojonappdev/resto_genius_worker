<template>
  <div>
    <form class="q-mx-md q-mb-lg column">
      <q-input class="q-mb-md" label="Email" v-model="loginFormData.email" />
      <q-input
        class="q-mb-lg"
        label="Password"
        v-model="loginFormData.password"
      />
      <q-btn to="/main" class="q-py-sm" color="primary">Kirish</q-btn>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const loginFormData = ref({
  email: '',
  password: '',
});
</script>

<style scoped lang="scss"></style>
