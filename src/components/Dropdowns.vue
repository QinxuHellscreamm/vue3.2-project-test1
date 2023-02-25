<script setup lang="ts">
import { defineProps, nextTick, onMounted, onUnmounted, ref } from "vue";
const title = defineProps({
  title: {
    type: String,
    required: true,
  },
});
const isShow = ref(false);

const dropdownRef = ref<null | HTMLElement>(null);
console.log(dropdownRef);
const handler = (e: MouseEvent) => {
  if (dropdownRef.value) {
    if (!dropdownRef.value.contains(e.target as HTMLElement) && isShow.value) {
      isShow.value = !isShow.value;
      nextTick(() => {
        isShow.value = !isShow.value;
      });
    }
  }
};
onMounted(() => {
  document.addEventListener("click", handler);
});
onUnmounted(() => {
  document.removeEventListener("click", handler);
});
</script>

<template>
  <div class="dropdown">
    <button
      class="btn btn-secondary dropdown-toggle"
      type="button"
      id="dropdownMenuButton"
      data-bs-toggle="dropdown"
      aria-expanded="false"
      @click.prevent="
        nextTick(() => {
          isShow = !isShow;
        })
      "
    >
      {{ title }}
    </button>
    <ul
      class="dropdown-menu show"
      aria-labelledby="dropdownMenuButton"
      v-show="isShow"
      ref="dropdownRef"
    >
      <li><a class="dropdown-item" href="#">Action</a></li>
      <li><a class="dropdown-item" href="#">Another action</a></li>
      <li><a class="dropdown-item" href="#">Something else here</a></li>
    </ul>
  </div>
</template>

<style scoped></style>
