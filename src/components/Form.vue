<script setup lang="ts">
import { reactive } from "vue";
import FormItem from '@/components/FormItem.vue'

const emailRef = reactive({
  val: "",
  error: false,
  msg: "",
});

</script>

<template>
  <div class="form">
    <div class="mb-3">
      <label for="staticEmail" class="col-sm-2 col-form-label">Email</label>
      <div class="col-sm-10">
      <FormItem v-model="emailRef.val" :rules="[{type:'email',required:true}]"></FormItem>
      </div>
    </div>
    <div class="mb-3">
      <label for="inputPassword" class="col-sm-2 col-form-label"
        >Password</label
      >
      <div class="col-sm-10">
        <input type="password" class="form-control" id="inputPassword" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.form {
  text-align: left;
}
</style>
