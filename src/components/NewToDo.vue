<template>
  <form @submit.prevent="addToDo()" class="col-12 col-lf-16">
    <input v-model="newName" placeholder="Enter Todo" type="text" class="form-control" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      newName: "",
    };
  },
  methods: {
    addToDo() {
      if (this.newName.length > 1) {
        this.$emit("on-addToDo", this.newName);
      }

      this.newName = "";
    },
  },
};
</script>

<style scoped>
</style>