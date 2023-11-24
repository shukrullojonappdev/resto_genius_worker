<template>
  <q-page class="column box">
    <div class="col column justify-center box-title">
      <p class="text-h3 q-ml-md">Sign in</p>
    </div>
    <div class="col column justify-center box-form">
      <LoginFormComponent></LoginFormComponent>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import LoginFormComponent from '../components/LoginFormComponent.vue';
</script>

<style scoped lang="scss">
.box {
  background: $primary;

  &-title {
    color: white;
    max-height: 150px;
  }

  &-form {
    border-radius: 10px 10px 0 0;
    background: #fff;
  }
}
</style>
