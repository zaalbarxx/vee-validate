<template>
  <input @input="handleChange" :value="value" type="text" />
  <span>{{ errorMessage }}</span>
</template>

<script setup>
import { useField } from '@zaalbarxx/vee-validate';

const props = defineProps({
  name: String,
  type: String,
});

const { errorMessage, value, handleChange } = useField(() => props.name);
</script>
