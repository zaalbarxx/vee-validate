<template>
  <input type="text" v-model="value" />
  {{ errorMessage }}
</template>

<script setup>
import { useField } from '@zaalbarxx/vee-validate';
import { toTypedSchema } from '@zaalbarxx/vee-validate-zod';
import { z } from 'zod';

const { value, errorMessage } = useField('email', toTypedSchema(z.string().email().min(1, 'Required')));
</script>
