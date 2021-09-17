<template>
  <li
    v-for="user in users"
    :key="user.id"
    class="p-4 mb-3 flex justify-between items-center bg-white shadow rounded-lg cursor-move"
  >
    <div class="flex items-center">
      <img
        class="w-10 h-10 rounded-full"
        :src="user.avatar"
        :alt="user.name"
      >
      <p class="ml-2 text-gray-700 font-semibold font-sans tracking-wide">{{user.name}}</p>
    </div>
    <div class="flex">
      <button
        aria-label="Edit user"
        class="p-1 focus:outline-none focus:shadow-outline text-teal-500 hover:text-teal-600 cursor-pointer"
        @click="onEdit(user)"
      >
        Editer
      </button>
      <button
        aria-label="Delete user"
        class="p-1 focus:outline-none ml-2 focus:shadow-outline text-white bg-red-500 rounded hover:text-red-600 hover:border-red hover:border-2 hover:bg-white cursor-pointer"
        @click="onDelete(user)"
      >
        Supprimer
      </button>
    </div>
  </li>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ListItem',
  props: {
    users: {
      type: Array,
      default: () => [],
    },
  },
  setup(_, { emit }) {
    function onEdit(user) {
      emit('edit', user)
    }
    function onDelete(user) {
      emit('delete', user)
    }
    return {
      onEdit,
      onDelete,
    }
  },
})
</script>
