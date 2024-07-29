<script setup>
const props = defineProps({
  resultado: [Number, String] 
});
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="mt-3">
          Resultado: {{ resultado }} 
        </div>
      </div>
    </div>
  </div>
</template>