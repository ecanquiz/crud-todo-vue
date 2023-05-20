<script lang="ts">
import { defineComponent } from 'vue'
import FormTask from '../components/FormTask.vue'
import useCreateOrEdit from '../composables/useCreateOrEdit'

export default defineComponent({
  props: {
    id: String
  },
  components: {
    FormTask
  },
  setup(props) {
    const {
      isRenderable,
      pending,
      task,
    
      submit
    } = useCreateOrEdit(props)

    return {
      isRenderable,
      pending,
      task,

      submit
    }
  }
})
</script>

<template>
  <div class="container row col-md-6 mx-auto w-1/2">
    <h1 v-if="pending" class="text-2xl" align="center">Loading...</h1>
    <h1 v-else class="text-2xl" align="center">
      {{$props.id ? 'Editing' : 'Creating'}} Tast
    </h1>
    <FormTask v-if="isRenderable" :task="task" @submit='submit' />
  </div>
</template>
