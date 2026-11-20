<script setup lang="ts">
import JSON5 from 'json5';
import _ from 'lodash';
import { convertArrayToCsv } from './json-to-csv.service';
import type { UseValidationRule } from '@/composable/validation';
import { withDefaultOnError } from '@/utils/defaults';

function toArrayOfObjects(json: unknown): Record<string, unknown>[] | undefined {
  // A single object is converted as a one-row CSV
  const array = _.isPlainObject(json) ? [json] : json;

  if (!Array.isArray(array) || !array.every(item => _.isPlainObject(item))) {
    return undefined;
  }

  return array;
}

function transformer(value: string) {
  return withDefaultOnError(() => {
    if (value === '') {
      return '';
    }

    const array = toArrayOfObjects(JSON5.parse(value));

    return array ? convertArrayToCsv({ array }) : '';
  }, '');
}

const rules: UseValidationRule<string>[] = [
  {
    validator: (v: string) => v === '' || JSON5.parse(v),
    message: 'Provided JSON is not valid.',
  },
  {
    validator: (v: string) => withDefaultOnError(() => v === '' || toArrayOfObjects(JSON5.parse(v)) !== undefined, true),
    message: 'Provided JSON must be an array of objects (or a single object).',
  },
];
</script>

<template>
  <format-transformer
    input-label="Your raw JSON"
    input-placeholder="Paste your raw JSON here..."
    output-label="CSV version of your JSON"
    :input-validation-rules="rules"
    :transformer="transformer"
  />
</template>
