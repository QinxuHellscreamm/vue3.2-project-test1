<script lang="ts" setup>
import { computed, defineProps, PropType } from "vue";
export interface itemProps {
  id: number;
  title: string;
  avatar?: string;
  description: string;
}
/*
 * PropType 专为vue 属性提供支持泛型的类型
 * */
const props = defineProps({
  list: {
    type: Array as PropType<itemProps[]>,
    required: true,
  },
});

const newList = computed(() => {
  return props.list.map((item) => {
    if (!item.avatar) {
      item.avatar = require("@/assets/logo.png");
    }
    return item;
  });
});
</script>

<template>
  <ul class="row">
    <li v-for="item in newList" :key="item.id" class="col-4">
      <div class="card h-100 shadow-sm">
        <img
          :src="item.avatar"
          :alt="item.title"
          class="rounded-circle w-25 m-auto"
        />
        <div class="card-body">
          <h5 class="card-title">{{ item.title }}</h5>
          <p class="card-text">{{ item.description }}</p>
          <a href="#" class="btn btn-outline-primary">进入</a>
        </div>
      </div>
    </li>
  </ul>
</template>

<style scoped></style>
