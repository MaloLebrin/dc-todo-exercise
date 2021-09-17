<template>
  <div
    id="app"
    class="min-h-screen w-screen bg-gray-200 flex items-center justify-center"
  >
    <ul class="w-full max-w-md">
      <!-- <li
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
      </li> -->
      <ListItem
        :users="elements"
        @delete="onDeleteUser"
      />
    </ul>
  </div>
</template>

<script>
import { ref, defineComponent } from 'vue'
import ListItem from './components/listItem.vue'
import users from '../users.json'

export default defineComponent({
  name: 'App',
  components: {
    ListItem,
  },
  setup() {
    const elements = ref(users)
    function onDeleteUser(userToDelete) {
      const newArrayOfUsers = elements.value.filter(user => user.id !== userToDelete.id)
      elements.value = newArrayOfUsers
    }

    return {
      onDeleteUser,
      elements,
    }
  },
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
