<script setup lang="ts">
useHead({
  title: "Login Page",
});

const email = ref("");
const password = ref("");

const isValid = computed(() => {
  return email.value && password.value;
});

const redirectTo = useAuth().redirectTo.value
const alert = ref(
  `Please login or register ${redirectTo ? `to access ${redirectTo}` : ""}`
);

const showAlert = (message: string) => {
  alert.value = message
  setTimeout(() => {
    alert.value = "";
  }, 1500);
}

const onError = (err: any) => {
  showAlert(err?.data.message ?? err?.message ?? err);
};
</script>

<template>
  <div>
    <div>
      <div>
        <div>
          <label for="email">Email</label>
          <UInput id="email" type="email" placeholder="Email" v-model="email" />
          <!-- <NTextInput id="email" type="email" placeholder="Email" v-model="email" /> -->
        </div>
        <div>
          <label for="password">Password</label>
          <UInput
            id="password"
            type="password"
            placeholder="Password"
            v-model="password" />
        </div>
      </div>
      <br />
      <NTip v-if="alert" n="orange">
        {{ alert }}
      </NTip>
      <br />
      <div>
        <UButton @click="authLogin(email, password).catch(onError)" :disabled="!isValid" class="mr-2">
          Login
        </UButton>
        <UButton @click="authRegister(email, password).catch(onError)" :disabled="!isValid" class="mr-2">
          Register
        </UButton>
      </div>
    </div>
  </div>
</template>
