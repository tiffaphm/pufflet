<script setup>
import { cn } from '@/lib/utils';

const props = defineProps({
  class: { type: null, required: false },
});
</script>

<template>
  <div
    :class="
      cn('tw-rounded-xl tw-border tw-border-neutral-200 tw-bg-white tw-text-neutral-950 tw-shadow dark:tw-border-neutral-800 dark:tw-bg-neutral-950 dark:tw-text-neutral-50', props.class)
    "
  >
    <slot />
  </div>
</template>
