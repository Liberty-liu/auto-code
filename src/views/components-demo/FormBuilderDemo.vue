<template>
  <div class="app-container">
    <FormBuilder />
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
import FormBuilder from '@/components/form-builder/Index.vue'
export default defineComponent({
  name: 'FormBuilderDemo',
  components: {
    FormBuilder
  },
  setup() {
    console.log('create')
  }
})
</script>

<style scoped>

</style>
