<template>
  <div class="mb-3">
    <label for="mail" class="form-label d-block">メールアドレス</label>
    <input 
      id="mail" 
      name="mail" 
      type="email" 
      class="form-controll" 
      :value="modelValue" 
      @change="$emit('update:modelValue', $event.target.value)"
    >
    <pre class="text-secondary">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventMail',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>