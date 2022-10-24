<template>
  <div>
    <p v-if="user">
      {{ user.email }}
    </p>
    <p v-else>Not logged in</p>
  </div>
</template>

<script setup lang="ts">
const user = useSupabaseUser();
</script>
