<template>
  <input v-model="value" :type="type || 'text'" />
  {{ errorMessage }}
</template>

<script setup>
import { useField } from '@zaalbarxx/vee-validate';

const props = defineProps({
  name: String,
  type: String,
  modelValue: String,
});

// The `name` is returned in a function because we want to make sure it stays reactive
// If the name changes you want `useField` to be able to pick it up
const { value, errorMessage } = useField(() => props.name, undefined, {
  syncVModel: true,
});
</script>
