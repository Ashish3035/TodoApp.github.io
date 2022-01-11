<template>
  <div class="grid place-items-center h-96">
    <div>
      <h1 class="text-xl">To-Do App</h1>
      <div v-if="!isEditing">
        <label class="block">
          <span
            class="
              after:content-['*'] after:ml-0.5 after:text-red-500
              block
              text-sm
              font-medium
              text-gray-700
            "
          >
            New To-Do
          </span>
          <input
            type="text"
            name="text"
            class="
              mt-1
              px-3
              py-2
              bg-white
              border
              shadow-sm
              border-gray-300
              placeholder-gray-400
              focus:outline-none focus:border-sky-500 focus:ring-sky-500
              block
              w-full
              rounded-md
              sm:text-sm
              focus:ring-1
            "
            v-model="todo"
          />
        </label>
        <button @click="storeData" class="bg-indigo-500 mt-2 px-5 ...">
          Add ToDo
        </button>
        <button @click="clearData" class="bg-indigo-500 mt-2 px-5 ml-9 ...">
          Clear All
        </button>
      </div>

      <div v-else>
        <label class="block">
          <span
            class="
              after:content-['*'] after:ml-0.5 after:text-red-500
              block
              text-sm
              font-medium
              text-gray-700
            "
          >
            New To-Do
          </span>
          <input
            type="text"
            name="text"
            class="
              mt-1
              px-3
              py-2
              bg-white
              border
              shadow-sm
              border-gray-300
              placeholder-gray-400
              focus:outline-none focus:border-sky-500 focus:ring-sky-500
              block
              w-full
              rounded-md
              sm:text-sm
              focus:ring-1
            "
            v-model="todo"
          />
        </label>
        <button @click="updateData" class="bg-indigo-500 mt-2 px-5 ...">
          Add ToDo
        </button>

        <clear-todo></clear-todo>
      </div>

      <div class="to-do-list">
        <h1 class="mt-6 text-xl ...">To-Do List</h1>
        <div class="border-b-4 border-indigo-500 ..."></div>

        <ul class="list-disc list-inside">
          <li v-for="(todo, index) in todos" :key="todo">
            {{ todo }}
            <button
              @click="editData(index, todo)"
              class="bg-red-200 mt-3 px-5 mx-px ..."
            >
              Edit
            </button>
            <button
              @click="removeData(index)"
              class="bg-indigo-200 mt-2 px-5 mx-px ..."
            >
              Remove
            </button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  data() {
    return {
      index: null,
      todo: "",
      isEditing: false,
      todos: [],
    };
  },
  methods: {
    storeData() {
      this.todos.push(this.todo);
      this.todo = "";
    },
    removeData(index) {
      this.todos.splice(index, 1);
    },
    editData(index, todo) {
      this.todo = todo;
      this.index = index;
      this.isEditing = true;
    },
    updateData() {
      this.todos.splice(this.index, 1, this.todo);
      this.isEditing = false;
      this.todo = "";
    },
    clearData() {
      this.todos = [];
    },
  },
};
</script>
