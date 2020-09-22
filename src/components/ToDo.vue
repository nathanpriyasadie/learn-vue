<template>
  <li class="d-flex align-items-center list-group-item">
    <button
      v-if="!isEditing"
      :class="{completed}"
      @click="$emit('on-toggle')"
      class="btn border-0 text-left flex-grow-1"
    >{{name}}</button>
    <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
      <input @blur="startEditing()" v-model="newName" type="text" class="form-control" />
    </form>
    <button @click="startEditing()" class="btn btn-outline-primary">Edit</button>
    <button @click="$emit('on-delete')" class="btn btn-outline-danger">Delete</button>
  </li>
</template>

<script>
export default {
  props: {
    name: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      newName: "",
    };
  },
  methods: {
    startEditing() {
      if (!this.isEditing) {
        this.newName = this.name;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      this.isEditing = false;
      this.$emit("on-edit", this.newName);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>