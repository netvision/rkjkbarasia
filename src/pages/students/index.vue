<script setup>
import { useRouter } from 'vue-router'
import { api } from '../../services/api'

const router = useRouter()

const goTo = (id) => {
  router.push({ path: 'students/'+id })
}
const batches = ref([])
const students = ref([])

async function getStudents(batchId) {
  students.value = await api.get(`student-batch?filter[batch_id][eq]=${batchId}&expand=student`).then(r => r.data)
}

onMounted(async () => {
  batches.value = await api.get('batch?expand=course,part').then(r => r.data)
  getStudents(1)
})
</script>

<template>
  <div class="flex">
    <!-- First Column -->
    <div class="w-1/4 p-4">
      <ul>
        <li v-for="batch in batches" :key="batch.id" class="hover:cursor-pointer hover:bg-blue-200" @click="getStudents(batch.id)">
          {{ batch.course.short_name }} {{ batch.part.title }}
        </li>
      </ul>
    </div>

    <!-- Second Column -->
    <div class="mb-14 w-3/4 p-4">
      <div class="grid grid-cols-2 m-6 gap-4 md:grid-cols-4">
        <div v-for="s in students" :key="s.id">
          <div @click="goTo(s.student.id)">
            <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
              {{ s.student.full_name }}
            </h5>
            <p>{{ s.student.current_address }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<route lang="json">
  {
    "meta" : {
      "requireAuth" : true
    }
  }
</route>