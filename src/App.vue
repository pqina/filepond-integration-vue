<script setup lang="ts">
// FilePond imports
import { defineFilePond, type FilePondEntry } from 'filepond';
import { locale } from 'filepond/locales/en-gb.js';

// Optionally import Vue <file-pond> component types
import 'filepond/types/vue';

// Defines <file-pond> custom element
defineFilePond({
    locale,
});

function handleEntriesChange(e: CustomEvent<FilePondEntry[]>) {
    console.log('entrieschange', e);
}

function handleSubmit(e: Event) {
    e.preventDefault();
    console.log('submit', e);
}
</script>

<template>
    <form @submit="handleSubmit" method="POST">
        <label for="my-file">Documents</label>

        <file-pond @entrieschange="handleEntriesChange" animations="auto">
            <input id="my-file" type="file" name="files" required multiple />
        </file-pond>

        <button type="submit">Upload</button>
    </form>
</template>

<style scoped>
form {
    font-family:
        system-ui,
        -apple-system,
        BlinkMacSystemFont,
        'Segoe UI',
        Roboto,
        Oxygen,
        Ubuntu,
        Cantarell,
        'Open Sans',
        'Helvetica Neue',
        sans-serif;
}
</style>
