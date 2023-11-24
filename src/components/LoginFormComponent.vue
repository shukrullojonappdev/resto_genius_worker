<template>
  <div>
    <form class="q-mx-md q-mb-lg">
      <q-input class="q-mb-md" label="Email" v-model="loginFormData.email" />
      <q-input
        class="q-mb-lg"
        label="Password"
        v-model="loginFormData.password"
      />
      <router-link to="/main">
        <q-btn class="q-py-sm" color="primary"> Login </q-btn>
      </router-link>
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

<style scoped lang="scss">
button {
  width: 100%;
}
</style>
