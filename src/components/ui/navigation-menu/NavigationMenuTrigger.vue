<script setup>
import { cn } from '@/lib/utils';
import { ChevronDownIcon } from '@radix-icons/vue';
import { NavigationMenuTrigger, useForwardProps } from 'reka-ui';
import { computed } from 'vue';
import { navigationMenuTriggerStyle } from '.';

const props = defineProps({
  disabled: { type: Boolean, required: false },
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
  <NavigationMenuTrigger
    v-bind="forwardedProps"
    :class="cn(navigationMenuTriggerStyle(), 'tw-group', props.class)"
  >
    <slot />
    <ChevronDownIcon class=""tw-relative tw-top-px tw-ml-1 tw-h-3 tw-w-3 tw-transition tw-duration-300 group-data-[state=open]:tw-rotate-180"" aria-hidden="true" />
  </NavigationMenuTrigger>
</template>
