<template>
  <div class="news-popup">
    <div class="news-popup-content">
      <div class="news-popup-content-breadcrumb"></div>
      <div class="news-popup-content-tags">
        <Tag
            v-for="(tag, i) in news.data.result.tags"
            :key="i"
            :tag="tag"
        ></Tag>
      </div>
      <div class="news-popup-content-title">
        <h1>{{ news.data.result.title }}</h1>
      </div>
      <div class="news-popup-content-date">

      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from "axios"

const route = useRoute()

async function getNews() {
  try {
    const response = await axios.get(import.meta.env.VITE_API_URL + "/news/" + route.params.slug)
    if (response.status === 200) {
      return response.data
    }
    else {
      return response.data.message[0]
    }
  } catch (e: any) {
    return e.response.data.message[0]
  }
}

const news = await getNews()


</script>

<style scoped lang="scss">
.news-popup {
  width: 95%;
  display: flex;
  justify-content: center;
  background: white;
  margin: 0 auto;
  border-radius: 16px 16px 0 0;
  padding: 32px 0 64px 0;

  &-content {
    width: 70%;
    display: flex;
    flex-direction: column;

    &-tags {
      display: flex;
      flex-direction: row;
      gap: 8px;
    }

    &-title {
      h1 {
        font-family: Unbounded, sans-serif;
        font-size: 48px;
        line-height: 56px;
        color: #423F3F;
      }
    }
  }
}

</style>