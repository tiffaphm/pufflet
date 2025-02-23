<script setup>
import { cn } from '@/lib/utils';
import { NavigationMenuList, useForwardProps } from 'reka-ui';
import { computed } from 'vue';

const props = defineProps({
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
  <NavigationMenuList
    v-bind="forwardedProps"
    :class="
      cn(
        'tw-group tw-flex tw-flex-1 tw-list-none tw-items-center tw-justify-center tw-gap-x-1',
        props.class,
      )
    "
  >
    <slot />
  </NavigationMenuList>
</template>
