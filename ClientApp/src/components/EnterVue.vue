<template>
  <div style="height: 10em"></div>
  <v-card class="mx-auto" max-width="70%">
    <v-list density="compact">
      <v-list-subheader>Добро пожаловать!</v-list-subheader>

      <v-list-item
        v-for="(item, i) in items"
        :id="item.id"
        :key="i"
        :value="item"
        color="green"
        height="9em"
        class="text-h5"
        @click="chooserole($event)"
      >
        <template #prepend>
          <v-icon :id="item.id" :icon="item.icon"></v-icon>
        </template>

        <v-list-item-title :id="item.id" class="text-h5">{{
          item.text
        }}</v-list-item-title>
      </v-list-item>
    </v-list>
  </v-card>
</template>

<script>
import { useRouter, useRoute } from 'vue-router'
import { ref } from 'vue'
import axios from 'axios'
export default {
  setup() {
    const router = useRouter()
    const name = ref('')

  

    axiosTest()
    const chooserole = (data) => {
      let a = data.target.id
      if (a == '') alert('Ошибка')
      router.push({ name: 'Login', params: { role: data.target.id } })
    }
    return {
      items: [
        { text: 'Измеритель', icon: 'mdi-scale', id: 'Measurer' },
        { text: 'Технолог', icon: 'mdi-pencil', id: 'Technologist' },
        { text: 'Администратор', icon: 'mdi-account', id: 'Admin' },
      ],
      name,
      chooserole,
    }
  },
}
</script>
