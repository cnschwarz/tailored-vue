<template>
  <button
    class="flex flex-row items-center justify-between gap-1 p-1 cursor-pointer
    transition-colors duration-200 ease-out"
    :name="name"
    @click="clickHandler">
    {{ label }}
    <slot />
  </button>

</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Button',
  components: {},
  props: {
    icon: {
      type: String,
    },
    icon2: {
      type: String,
    },
    label: {
      type: String,
      default: '',
    },
    name: {
      type: String,
      default: () => 'button1',
    },
    readonly: {
      type: Boolean,
      default: false,
    },
  },
  emits: ['click'],
  setup(props, { emit }) {
    const clickHandler = () => {
      if (!props.readonly) {
        emit('click');
      }
    };
    return { clickHandler };
  },
});
</script>
