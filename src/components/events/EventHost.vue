<template>
  <div class="mb-3">
    <label for="host" class="form-label d-block">主催者</label>
    <input 
      id="host" 
      name="host" 
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
  name: 'EventHost',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>