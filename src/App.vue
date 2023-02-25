<script lang="ts" setup>
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnProps, { itemProps } from "@/components/ColumnProps";
import Nav from "@/components/Nav.vue";
import Form from "@/components/Form.vue";
const testListData: itemProps[] = [
  {
    id: 1,
    title: "test1的专栏",
    description:
      "这里是test1的专栏test1的专栏test1的专栏test1的专栏test1的专栏",
  },
  {
    id: 2,
    title: "test2的专栏",
    description:
      "这里是test2的专栏test2的专栏test2的专栏test2的专栏test2的专栏",
  },
];
</script>

<template>
  <Nav></Nav>
  <!--  <nav>-->
  <!--    <router-link to="/">Home</router-link> |-->
  <!--    <router-link to="/about">About</router-link>-->
  <!--  </nav>-->
  <router-view />
  <ColumnProps :list="testListData"></ColumnProps>
  <Form></Form>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
