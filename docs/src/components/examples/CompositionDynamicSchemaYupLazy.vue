<script setup>
import { ref } from 'vue';
import { useForm } from '@zaalbarxx/vee-validate';
import { toTypedSchema } from '@zaalbarxx/vee-validate-yup';
import * as yup from 'yup';

const limit = ref(5);

const { errors, defineField } = useForm({
  validationSchema: toTypedSchema(
    yup.lazy(() =>
      yup.object({
        content: yup.string().max(limit.value),
      }),
    ),
  ),
});

const [content, contentAttrs] = defineField('content');
</script>

<template>
  <input v-model.number="limit" />

  <input v-model="content" v-bind="contentAttrs" />
  <div>{{ errors.content }}</div>
</template>
