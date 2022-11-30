<template>
  <label>
    {{ props.texto }}
    <input type="file" @change="loadTextFromFile" />
  </label>
</template>

<script setup>
const props = defineProps({
  texto: {
    type: String,
  },
});

const emits = defineEmits(["carga"]);

const loadTextFromFile = (ev) => {
  const file = ev.target.files[0];
  const reader = new FileReader();
  reader.onload = (e) => emits("carga", e.target.result);
  reader.readAsText(file);
};
</script>

<style></style>
