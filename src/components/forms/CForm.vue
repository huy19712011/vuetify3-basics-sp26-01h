<template>
  <v-sheet
    class="mx-auto"
    width="300">
    <v-form
      @submit.prevent="submit">
      <v-text-field
        v-model="form.email"
        label="Email"
        variant="solo"
        prepend-inner-icon="mdi-mail"
      ></v-text-field>
      <v-text-field
        v-model="form.password"
        label="Password"
        variant="solo"
        prepend-inner-icon="mdi-key"
        type="password"
      ></v-text-field>

      <v-checkbox
        v-model="form.remember"
        color="blue"
        label="Remember Me"
        hide-details
      ></v-checkbox>
      <v-btn
        color="blue"
        class="mt-2"
        type="submit"
        block>
        Submit
      </v-btn>
    </v-form>
  </v-sheet>
</template>
<script setup>
const form = ref({
  email: "",
  password: "",
  remember: false,
});

function submit() {

  alert(JSON.stringify(form.value));
}
</script>
