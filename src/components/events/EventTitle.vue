<template>
  <div class="mb-3">
    <label for="title" class="form-label d-block">タイトル</label>
    <input 
      id="title" 
      name="title" 
      type="text" 
      class="form-controll" 
      :value="modelValue" 
      @input="$emit('update:modelValue', $event.target.value)"
    >
    <pre class="text-secondary">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventTitle',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>