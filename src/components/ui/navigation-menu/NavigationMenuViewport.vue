<script setup>
import { cn } from '@/lib/utils';
import { NavigationMenuViewport, useForwardProps } from 'reka-ui';
import { computed } from 'vue';

const props = defineProps({
  forceMount: { type: Boolean, required: false },
  align: { type: String, required: false },
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
  <div class="tw-absolute tw-left-0 tw-top-full tw-flex tw-justify-center">
    <NavigationMenuViewport
      v-bind="forwardedProps"
      :class="
        cn(
          'tw-origin-top-center tw-relative tw-mt-1.5 tw-h-[--reka-navigation-menu-viewport-height] tw-w-full tw-overflow-hidden tw-rounded-md tw-border tw-border-neutral-200 tw-bg-white tw-text-neutral-950 tw-shadow data-[state=open]:tw-animate-in data-[state=closed]:tw-animate-out data-[state=closed]:tw-zoom-out-95 data-[state=open]:tw-zoom-in-90 md:tw-w-[--reka-navigation-menu-viewport-width] dark:tw-border-neutral-800 dark:tw-bg-neutral-950 dark:tw-text-neutral-50',
          props.class,
        )
      "
    />
  </div>
</template>
