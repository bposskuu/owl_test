<template>
  <div class="tag" :color=props.tag.values[0].color>
    <span>{{ props.tag.values[0].name }}</span>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  tag: {
    type: Object,
    required: true
  },
})

</script>

<style scoped>

.tag {
  padding: 4px 12px;
  border: 1px solid;
  border-radius: 20px;
}

.tag[color=red] {
  color: #CA2250;
  border-color: #CA2250;
}

.tag[color=blue] {
  color: #5B4481;
  border-color: #5B4481;
}

</style>