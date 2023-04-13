<template>
  <div class="mb-3">
    <p class="fw-bold">【開催場所】</p>
    <div class=""><!-- 複数選択の場合、multiple -->
      <select 
        name="venue" 
        class="form-select" 
        aria-label="都道府県の選択" 
        :value="modelValue" 
        @change="$emit('update:modelValue', $event.target.value)"
      >
        <option selected>選択してください</option><!-- 無効表示選択の場合、disabled -->
        <option 
          v-for="location in locations" 
          :key="location"
          :value="location"
        >{{ location }}</option>
      </select>
    </div>
    <pre class="text-secondary">{{ modelValue }}</pre>
    <hr>
  </div>
</template>

<script>
// import ~~
export default {
  name: 'EventLocations',
  data: () => ({
    locations : [ '東京', 
                  '大阪', 
                  '名古屋',
    ],
    location  : '選択してください',
  }),
  props : ['modelValue', ],
  emits : ['update:modelValue',],
}
</script>

<style scoped>

</style>