<template>
  <div class="mb-3">
    <label for="maxNumber" class="form-label d-block">最大値</label>
    <input 
      id="maxNnumber" 
      name="maxNnumber" 
      type="number" 
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
  name: 'EventMaxNumber',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>