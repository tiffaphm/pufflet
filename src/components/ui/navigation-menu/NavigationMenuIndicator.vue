<script setup>
import { cn } from '@/lib/utils';
import { NavigationMenuIndicator, useForwardProps } from 'reka-ui';
import { computed } from 'vue';

const props = defineProps({
  forceMount: { type: Boolean, required: false },
  asChild: { type: Boolean, required: false },
  as: { type: null, required: false },
  class: { type: null, required: false },
});

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;

  return delegated;
});

const forwardedProps = useForwardProps(delegatedProps);
</script>

<template>
  <NavigationMenuIndicator
    v-bind="forwardedProps"
    :class="
      cn(
        'tw-top-full tw-z-[1] tw-flex tw-h-1.5 tw-items-end tw-justify-center tw-overflow-hidden data-[state=visible]:tw-animate-in data-[state=hidden]:tw-animate-out data-[state=hidden]:tw-fade-out data-[state=visible]:tw-fade-in',
        props.class,
      )
    "
  >
    <div
      class="tw-relative tw-top-[60%] tw-h-2 tw-w-2 tw-rotate-45 tw-rounded-tl-sm tw-bg-neutral-200 tw-shadow-md dark:tw-bg-neutral-800"
    />
  </NavigationMenuIndicator>
</template>
