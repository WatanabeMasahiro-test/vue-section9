<template>
  <div class="mb-3">
    <p class="fw-bold">【参加費】</p>
    <div class="form-check">
      <input 
        id="participation-free" 
        name="participation-fee" 
        type="radio" 
        class="form-check-input" 
        :value="value" 
        @change="$emit('update:modelValue', $event.target.value)"
        checked 
      >
      <label class="form-check-label" for="participation-free">無料</label>
    </div>
    <div class="form-check">
      <input 
        id="participation-paid" 
        name="participation-fee" 
        type="radio" 
        class="form-check-input" 
        :value="value" 
        @change="$emit('update:modelValue', $event.target.value)"
      >
      <label class="form-check-label" for="participation-paid">有料</label>
    </div>
    <pre class="text-secondary">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventParticipation',
  data: () => ({

  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>