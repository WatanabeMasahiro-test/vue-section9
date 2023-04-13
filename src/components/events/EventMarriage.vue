<template>
  <div class="mb-3">
    <!-- checkedの代わりに、v-modelのデータをtrueにする -->
    <div class="form-check form-switch">
      <input 
        id="marriage-select" 
        name="marriage-select" 
        type="checkbox" 
        class="form-check-input" 
        @input="$emit('update:modelValue', $event.target.value)"
      >
      <label class="form-check-label" for="marriage-select">結婚歴</label>
    </div>
    <pre class="text-secondary">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventMarriage',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>