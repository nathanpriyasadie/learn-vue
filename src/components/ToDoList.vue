<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <p class="display-3">Vue To Do List</p>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <NewToDo @on-addToDo="addToDo($event)" />
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <ToDo
            v-for="(toDo, index) in toDos"
            :key="index"
            :name="toDo.name"
            :completed="toDo.completed"
            @on-delete="deleteToDo(toDo)"
            @on-toggle="toggleToDo(toDo)"
            @on-edit="editToDo(toDo,$event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import ToDo from "./ToDo";
import NewToDo from "./NewToDo";
export default {
  components: {
    ToDo,
    NewToDo,
  },
  data() {
    return {
      toDos: [
        { name: "belanja", completed: true },
        { name: "belajar", completed: false },
        { name: "joget", completed: true },
        { name: "hujan", completed: false },
      ],
    };
  },
  methods: {
    addToDo(newToDo) {
      this.toDos.push({
        name: newToDo,
        completed: false,
      });
    },
    toggleToDo(toDo) {
      toDo.completed = !toDo.completed;
    },
    editToDo(toDo, newName) {
      toDo.name = newName;
    },
    deleteToDo(deleteToDo) {
      this.toDos = this.toDos.filter((toDo) => toDo !== deleteToDo);
    },
  },
};
</script>

<style>
</style>