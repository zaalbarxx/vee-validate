<template>
  <input type="text" v-model="value" />
  {{ errorMessage }}
</template>

<script setup>
import { useField } from '@zaalbarxx/vee-validate';
import { toTypedSchema } from '@zaalbarxx/vee-validate-valibot';
import * as v from 'valibot';

const { value, errorMessage } = useField(
  'email',
  toTypedSchema(v.pipe(v.string(), v.email('Invalid email'), v.nonEmpty('Required'))),
);
</script>
