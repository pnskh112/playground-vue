<template>
  <div class="app-checkbox">
    <label>
      <input type="checkbox" v-model="items" :value="value" />
      {{ label }}
    </label>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
export default defineComponent({
  props: {
    modelValue: {
      type: [Array, Boolean],
      default: () => [],
    },
    value: {
      type: Number,
      default: 0,
    },
    label: {
      type: String,
      default: '',
    },
  },
  emits: ['update:modelValue'],
  setup(props, { emit }) {
    const items = computed({
      get: () => props.modelValue,
      set: (val) => emit('update:modelValue', val),
    });
    return {
      items,
    };
  },
});
</script>

<style scoped></style>
