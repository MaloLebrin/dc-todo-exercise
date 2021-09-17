<template>
  <div
    id="app"
    class="min-h-screen w-screen bg-gray-200 flex items-center justify-center"
  >
    <div>
      <div class="mb-8 flex flex-col justify-between">
        <h2 class="text-3xl font-semibold mb-2">Ajouter un user</h2>
        <input
          v-model="name"
          class="p-2 border rounded text-grey disabled:border-grey disabled:bg-grey-light focus:outline-none"
          type="test"
          placeholder="Nom"
        />
        <input
          v-model="url"
          class="p-2 border rounded text-grey disabled:border-grey disabled:bg-grey-light focus:outline-none"
          type="test"
          placeholder="Url de l'image"
        />

        <button
          class="bg-blue-800 text-white p-2 hover:text-blue-800 hover:border-red hover:border-2 hover:bg-white uppercase rounded cursor-pointer disabled:cursor-not-allowed mt-4"
          @click="addUser"
        >
          Enregistrer
        </button>

      </div>
      <ul class="w-full max-w-md">
        <ListItem
          v-for="user in elements"
          :id="user.id"
          :user="user"
          :key="user.id"
          @delete="onDeleteUser"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import { toRefs, defineComponent, reactive } from 'vue'
import ListItem from './components/listItem.vue'
import users from '../users.json'

export default defineComponent({
  name: 'App',
  components: {
    ListItem,
  },
  setup() {
    const data = reactive({
      elements: users,
      name: '',
      url: '',
    })
    function onDeleteUser(userToDelete) {
      const newArrayOfUsers = data.elements.filter(user => user.id !== userToDelete.id)
      data.elements.value = newArrayOfUsers
    }

    function addUser() {
      data.elements.push({ name: data.name, avatar: data.url })
    }

    return {
      ...toRefs(data),
      onDeleteUser,
      addUser,
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
