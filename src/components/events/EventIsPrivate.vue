<template>
  <div class="mb-3">
    <div class="form-check">
      <input 
        id="isPrivate" 
        name="checkbox" 
        type="checkbox" 
        class="form-check-input" 
        @change="$emit('update:modelValue', $event.target.value)" 
      >
      <label class="form-check-label" for="isPrivate">非公開</label>
      <pre class="text-secondary">{{ modelValue }}</pre>
    </div>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventIsPrivate',
  data: () => ({

  }),
  methods: {

  },
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>