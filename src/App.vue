<template>
  <div>
    <ToDoList />
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList";
export default {
  name: "App",
  components: {
    ToDoList,
  },
};
</script>

<style>
body {
  background-color: rgb(66, 66, 66);
  color: aliceblue;
}
</style>