<script lang="ts">
import { defineComponent } from 'vue'
import useFormTask from '../composables/useFormTask'

export default defineComponent({
  props: {
    task: Object    
  },
  emits: ['submit'],
  setup(props, ctx) {
    const {
      form,
      submit
    } = useFormTask(props, ctx)

    return {
      form,
      submit
    }
  }
})
</script>

<template>
  <form @submit.prevent="submit">
    <div class="m-2">
      <label>Title</label>
      <input type="text" v-model="form.title">
    </div>

   <div class="m-4">
      <label>Description</label>
      <textarea v-model="form.description"></textarea>
    </div>

    <div class="m-4">
      <label>Done</label>
      <input type="checkbox" v-model="form.done"/>
    </div>

    <button type="submit" class="btn btn-primary m-2">
      Save
    </button>
  </form>
</template>
