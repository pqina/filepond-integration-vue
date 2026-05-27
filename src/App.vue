<script setup lang="ts">
// filepond imports
import { defineFilePond } from "filepond";
import { locale } from "filepond/locales/en-gb.js";

// defines <file-pond> element
defineFilePond({
  locale,
});

function handleChange(e: Event) {
  console.log("change", e);
}

function handleSubmit(e: Event) {
  e.preventDefault();
  console.log("submit", e);
}
</script>

<template>
  <form @submit="handleSubmit" method="POST">
    <label for="my-file">Documents</label>

    <file-pond @change="handleChange">
      <input id="my-file" type="file" name="files" required multiple />
    </file-pond>

    <button type="submit">Upload</button>
  </form>
</template>

<style scoped></style>
