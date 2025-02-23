<script setup>
import { cn } from '@/lib/utils';
import { NavigationMenuContent, useForwardPropsEmits } from 'reka-ui';
import { computed } from 'vue';

const props = defineProps({
  forceMount: { type: Boolean, required: false },
  disableOutsidePointerEvents: { type: Boolean, required: false },
  asChild: { type: Boolean, required: false },
  as: { type: null, required: false },
  class: { type: null, required: false },
});

const emits = defineEmits([
  'escapeKeyDown',
  'pointerDownOutside',
  'focusOutside',
  'interactOutside',
]);

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;

  return delegated;
});

const forwarded = useForwardPropsEmits(delegatedProps, emits);
</script>

<template>
  <NavigationMenuContent
    v-bind="forwarded"
    :class="
      cn(
        'tw-left-0 tw-top-0 tw-w-full data-[motion^=from-]:tw-animate-in data-[motion^=to-]:tw-animate-out data-[motion^=from-]:tw-fade-in data-[motion^=to-]:tw-fade-out data-[motion=from-end]:tw-slide-in-from-right-52 data-[motion=from-start]:tw-slide-in-from-left-52 data-[motion=to-end]:tw-slide-out-to-right-52 data-[motion=to-start]:tw-slide-out-to-left-52 md:tw-absolute md:tw-w-auto',
        props.class,
      )
    "
  >
    <slot />
  </NavigationMenuContent>
</template>
