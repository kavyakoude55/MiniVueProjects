<template>
  <div class="p-4 max-w-md">
    <h2 class="text-xl font-semibold mb-4">User Form</h2>
    <form @submit.prevent="submitForm">
      <div class="mb-4">
        <label>Name:</label>
        <input
          v-model="name"
          type="text"
          class="border p-2 w-full"
        />
        <p v-if="nameError" class="text-red-500 text-sm">{{ nameError }}</p>
      </div>

      <div class="mb-4">
        <label>Email:</label>
        <input
          v-model="email"
          type="email"
          class="border p-2 w-full"
        />
        <p v-if="emailError" class="text-red-500 text-sm">{{ emailError }}</p>
      </div>

      <div class="mb-4">
        <label>Age:</label>
        <input
          v-model.number="age"
          type="number"
          class="border p-2 w-full"
        />
        <p v-if="ageError" class="text-red-500 text-sm">{{ ageError }}</p>
      </div>

      <button
        type="submit"
        :disabled="!isFormValid"
        class="bg-blue-500 text-white px-4 py-2 disabled:opacity-50"
      >
        Submit
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "FormValidation",
  data() {
    return {
      name: "",
      email: "",
      age: null,
    };
  },
  computed: {
    nameError() {
      return this.name.length < 2 ? "Name must be at least 2 characters." : "";
    },
    emailError() {
      const valid = /\S+@\S+\.\S+/.test(this.email);
      return !valid ? "Enter a valid email." : "";
    },
    ageError() {
      return this.age <= 0 || !this.age ? "Enter a valid age." : "";
    },
    isFormValid() {
      return !this.nameError && !this.emailError && !this.ageError;
    },
  },
  methods: {
    submitForm() {
      alert(`Submitted: ${this.name}, ${this.email}, ${this.age}`);
      this.name = "";
      this.email = "";
      this.age = null;
    },
  },
};
</script>

<style scoped>
</style>