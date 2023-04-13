<template>
  <div class="mb-3">
    <p class="fw-bold">【参加条件】</p>
    <div class="form-check form-check-inline">
      <input 
        id="teenager" 
        name="age" 
        type="checkbox" 
        class="form-check-input" 
        @input="$emit('update:modelValue', $event.target.value)"
      >
      <label class="form-check-label" for="teenager">10代</label>
    </div>
    <div class="form-check form-check-inline">
      <input 
        id="twenties" 
        name="age" 
        type="checkbox" 
        class="form-check-input" 
        @input="$emit('update:modelValue', $event.target.value)"
      >
      <label class="form-check-label" for="twenties">20代</label>
    </div>
    <div class="form-check form-check-inline">
      <input 
        id="thirties" 
        name="age" 
        type="checkbox" 
        class="form-check-input" 
        @input="$emit('update:modelValue', $event.target.value)"
      >
      <label class="form-check-label" for="thirties">30代</label>
    </div>
    <pre class="text-secondary">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventAgeConditions',
  data: () => ({
    ageTarget : [],
  }),
  computed: {
    alertAge() {
      var result = '';
      for(let i = 0 ; i < this.eventData.ageTarget.length; ++i) {
        result = ', ' + this.eventData.ageTarget;
      }
      return alert(result.replace(', ' , ''));
    },
  },
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>