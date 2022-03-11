<template>
<div style="display: flex; justify-content: center; margin: 2rem">
  <form @submit.prevent="onSubmit">
    <v-text-field
      v-model="title"
      label="New item"
      placeholder="Enter a new item for the todo list"
      filled
      outlined
      rounded
      dense
    ></v-text-field>
    <v-btn class="btn-send" type="submit" rounded color="primary"> Create an item </v-btn>
  </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };

        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  width: 35rem;
  justify-content: center;
  align-items: center;
}

btn-send {
  color: black;
}

.v-btn:not(.v-btn--round).v-size--default{
  color: black;
  background-color: #9eb8bf;
  margin: 0 0 1.5rem 3rem;
}
</style>
