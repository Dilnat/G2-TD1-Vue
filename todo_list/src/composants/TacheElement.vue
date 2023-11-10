<script setup lang="ts">
import {ref} from 'vue';
const props = defineProps<{descriptionTache: string, cochee:boolean}>();
const emit = defineEmits<{supprimerTache:[],
  checkedChange:[boolean]}>();



</script>

<template>
  <input type ="checkbox" :checked="props.cochee" @change="$emit('checkedChange', ($event.target as HTMLInputElement).checked)">
  <span :class="{fait: props.cochee}">{{props.descriptionTache}}</span>
  <button @click="$emit('supprimerTache')" >Retirer</button>
</template>

<style scoped>
.fait{
  text-decoration: line-through;
}
</style>

