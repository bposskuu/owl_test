<template>
  <div class="tag" :color=props.tag.values[0].color>
    <img :src="tag.values[0].src" v-if="tag.values[0].src" alt="">
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
  padding: 4rem 12rem;
  border: 1rem solid;
  border-radius: 20rem;
  display: flex;
  align-items: center;
  gap: 4rem;

  @media (max-width: 768px) {
    & {
      padding: 8rem 24rem;
      border-radius: 32rem;
    }
  }

  span {
    font-size: 14rem;

    @media (max-width: 768px) {
      & {
        font-size: 24rem;
      }
    }
  }

  img {
    height: 18rem;
    width: 18rem;

    @media (max-width: 768px) {
      & {
        width: 32rem;
        height: 32rem;
      }
    }
  }
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