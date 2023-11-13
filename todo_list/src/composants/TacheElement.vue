<script setup lang="ts">
import {ref} from 'vue';
const props = defineProps<{descriptionTache: string, modelValue:boolean}>();
const emit = defineEmits<{supprimerTache:[],
  "update:modelValue": [nouvelleValeur: boolean]}>();



</script>

<template>
  <input type="checkbox" :checked="modelValue"
         @change="$emit('update:modelValue', ($event.target as HTMLInputElement).checked)"
  />
  <span :class="{fait: props.modelValue}">{{props.descriptionTache}}</span>
  <button @click="$emit('supprimerTache')" >Retirer</button>
</template>

<style scoped>
.fait{
  text-decoration: line-through;
}
</style>

