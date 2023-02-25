<script setup lang="ts">
import { reactive } from "vue";

const emailRef = reactive({
  val: "",
  error: false,
  msg: "",
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
</script>

<template>
  <div class="form">
    <div class="mb-3">
      <label for="staticEmail" class="col-sm-2 col-form-label">Email</label>
      <div class="col-sm-10">
        <input
          type="email"
          class="form-control"
          id="staticEmail"
          v-model="emailRef.val"
          @blur="validateEmail"
        />
        <div class="form-text">{{ emailRef.msg }}</div>
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
