<script setup>
import { api } from '../../services/api'

const props = defineProps(['id'])
const student = ref({})

onMounted(async () => {
  student.value = await api.get(`students/${props.id}`).then(r => r.data)
})
</script>

<template>
  <div class="flex">
    <!-- First Column -->
    <div class="w-1/4 p-4">
      <p>Left menu</p>
    </div>

    <!-- Second Column -->
    <div class="w-3/4 p-4">
      <pre>{{ student }}</pre>
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
