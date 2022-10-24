<template>
  <div>
    <form @submit.prevent="login">
      <input v-model="email" type="text" placeholder="E-Mail" required />
      <input v-model="password" type="password" placeholder="Password" required />
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script setup lang="ts">
const supabase = useSupabaseClient();

const email = ref("");
const password = ref("");

const login = async () => {
  try {
    const { error } = await supabase.auth.signInWithPassword({
      email: email.value,
      password: password.value,
    });

    if (error) throw error;

    navigateTo("/user");
    console.log("Successfully logged in");
  } catch (error) {
    console.log(error.error_description || error.message);
  }
};
</script>
