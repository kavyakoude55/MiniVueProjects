<template>
  <div class="p-4 bg-black text-white">
    <label class="block mb-2">Password:</label>
    <input
      :type="showPassword ? 'text' : 'password'"
      v-model="password"
      class="border p-2 w-64"
    />
    <div class="mt-2">
      <input type="checkbox" id="toggle" v-model="showPassword" />
      <label for="toggle">Show Password</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "ShowHidePassword",
  data() {
    return {
      password: "",
      showPassword: false,
    };
  },
};
</script>

<style scoped>
</style>
