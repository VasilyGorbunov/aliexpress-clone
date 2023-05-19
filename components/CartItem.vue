<template>
  <div class="flex justify-start my-2">
    {{ product }}
  </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user';
const userStore = useUserStore();

const props = defineProps(['product', 'selectedArray']);
const { product, selectedArray } = toRefs(props);

const emit = defineEmits(['selectedRadio']);

const isHover = ref(false);
const isSelected = ref(false);

const remoceFromCart = () => {
  userStore.cart.forEach((prod, index) => {
    if (prod.id === product.value.id) {
      userStore.cart.splice(index, 1);
    }
  });
};
</script>