<template>
  <div class="mb-3">
    <label for="detail" class="form-label d-block">イベントの内容</label>
    <textarea 
      id="detail" 
      name="detail" 
      cols="15" 
      rows="5" 
      class="form-controll d-inline-block mx-1" 
      :value="modelValue" 
      @input="$emit('update:modelValue', $event.target.value)"
    ></textarea>
    <pre class="text-secondary d-inline-block align-top mx-1">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventDetail',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>