<template>
  <div class="breadcrumbs">
    <div class="breadcrumbs-item with-next">
      <NuxtLink to="/">ГЛАВНАЯ</NuxtLink>
    </div>
    <div class="breadcrumbs-item with-next"
         v-for="(path, i) in paths"
         :key="i">
      <NuxtLink :to="`/${path}`">{{ path.toUpperCase() }}</NuxtLink>
    </div>
    <div class="breadcrumb-item last-item">
      {{ props.pageName.toUpperCase() }}
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  pageName: {
    type: String,
    required: true
  },
})

const route = useRoute()
const paths = route.path.split('/')
paths.pop()
paths.shift()
</script>

<style scoped lang="scss">
.breadcrumbs {
  display: flex;
  flex-direction: row;
  align-items: center;

  &-item {
    display: flex;
    align-items: center;

    a {
      color: #423F3F;
    }
  }

  .with-next:after {
    display: inline-flex;
    content: "";
    width: 4px;
    height: 4px;
    border-radius: 100%;
    background-color: #423F3F;
    margin: 0 10px;
    align-items: center;
  }

  .last-item {
    color: #423F3F;
    opacity: 40%;
  }
}




</style>