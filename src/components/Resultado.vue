<script setup>
const props = defineProps({
  resultado: [Number, String] // Adicione os tipos esperados para a prop
});
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="mt-3">
          Resultado: {{ props.resultado }}
        </div>
      </div>
    </div>
  </div>
</template>