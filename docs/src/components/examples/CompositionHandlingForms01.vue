<script setup>
import { useForm } from '@zaalbarxx/vee-validate';

const { meta, defineField } = useForm();

const [name, nameAttrs] = defineField('name');
</script>

<template>
  <input v-model="name" v-bind="nameAttrs" />

  <button :disabled="!meta.touched">Submit</button>
</template>
