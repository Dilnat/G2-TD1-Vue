<script setup lang="ts">
const props = defineProps<{modelValue:boolean}>();
defineEmits<{supprimerTache:[],
  "update:modelValue": [nouvelleValeur: boolean]}>();



</script>

<template>
  <input type="checkbox" :checked="modelValue"
         @change="$emit('update:modelValue', ($event.target as HTMLInputElement).checked)"
  />
  <span :class="{fait: props.modelValue}"><slot></slot></span>
  <button @click="$emit('supprimerTache')" >Retirer</button>
</template>

<style scoped>
.fait{
  text-decoration: line-through;
}
</style>

