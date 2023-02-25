<script setup lang="ts">
import { defineProps, ref } from "vue";
interface propRule {
  type: "email";
  required: boolean;
}
const props = defineProps({
  rulus: Array as propRule[],
  value: String,
});

const emailReg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/;
const validateEmail = () => {
  console.log(emailReg.test(emailRef.val));
  if (emailRef.val.trim() === "") {
    emailRef.msg = "can not be empty";
    emailRef.error = true;
  } else if (!emailReg.test(emailRef.val)) {
    emailRef.msg = "valid email";
    emailRef.error = true;
  } else {
    emailRef.error = false;
    emailRef.msg = "";
  }
};

const emit = defineEmits<{
  (event: "change", val: string): void;
}>();

const emitChange = () => {
  // emit('change',value.value)
  console.log(value.value);
  props.value = value.value
};
// watch
console.log(props);
const value = ref(props.value);
</script>

<template>
  <input
    type="email"
    class="form-control"
    id="staticEmail"
    :class="{'is-invalid' : isPass}"
    v-model="value"
    @change="props.value = value"
    @blur=""
  />
  <div id="validationServer03Feedback" class="invalid-feedback">
    Please provide a valid city.
  </div>
</template>

<style scoped></style>
