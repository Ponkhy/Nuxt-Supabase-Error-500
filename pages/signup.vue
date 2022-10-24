<template>
  <div>
    <form @submit.prevent="signup">
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

const signup = async () => {
  try {
    const { error } = await supabase.auth.signUp({
      email: email.value,
      password: password.value,
    });

    if (error) throw error;

    navigateTo("/login");
    console.log("Successfully signed up");
  } catch (error) {
    console.log(error.error_description || error.message);
  }
};
</script>
