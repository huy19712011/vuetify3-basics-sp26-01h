<template>
  <v-sheet
    class="mx-auto"
    width="300">
    <v-form
      v-model="formIsValid"
      @submit.prevent="submit"
      ref="form">
      <v-text-field
        v-model="formData.email"
        label="Email"
        variant="solo"
        prepend-inner-icon="mdi-mail"
        :rules="inputRules">
      </v-text-field>
      <v-text-field
        v-model="formData.password"
        type="password"
        label="Password"
        variant="solo"
        prepend-inner-icon="mdi-key"
        :rules="inputRules"
        validate-on="lazy">
      </v-text-field>

      <v-checkbox
        v-model="formData.remember"
        color="blue"
        label="Remember Me"
        hide-details>
      </v-checkbox>
      <v-btn
        :disabled="!formIsValid"
        color="blue"
        class="mt-2"
        type="submit"
        block>
        Submit
      </v-btn>
    </v-form>
  </v-sheet>
</template>
<!---->
<script setup lang="ts">
import {VForm} from "vuetify/components";

const formData = ref({
  email: "",
  password: "",
  remember: false,
});

const inputRules = [
  (value: string) => !!value || "Required",
  (value: string) => value.length >= 3 || "Minimum length is 3 characters",
];

const form = ref<VForm | null>(null);
// const form = ref();
const formIsValid = ref(false);

async function submit() {
  // 1. Destructure 'errors' along with 'valid'
  const {valid, errors} = await form.value.validate();

  if (valid) {
    alert(JSON.stringify(formData.value));
  } else {
    // Note: for learning only, this button disabled => never show on console. To see => remove attribute :disabled="!formIsValid" in v-button
    // 2. Log the errors array to the console
    console.log("Validation failed!", errors);

    // Optional: Log only the specific error messages
    const messages = errors.map(e => `${e.id}: ${e.errorMessages[0]}`);
    console.table(messages);
  }
}
</script>
