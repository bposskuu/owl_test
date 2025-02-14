<template>
  <div class="news-popup">
    <div class="news-popup-content">
      <div class="news-popup-header">
        <div class="news-popup-header-breadcrumb">
          <Breadcrumbs :page-name=news.data.result.title />
        </div>
        <div class="news-popup-header-tags">
          <Tag
              v-for="(tag, i) in news.data.result.tags"
              :key="i"
              :tag="tag"
          />
        </div>
        <div class="news-popup-header-title">
          <h1>{{ news.data.result.title }}</h1>
        </div>
        <div class="news-popup-header-date">
          <span>{{ news.data.result.date.replaceAll('-', '.') }}</span>

        </div>
      </div>
      <NextNews :next-news="news.data.result.next" />
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from "axios"
import Breadcrumbs from "~/components/Breadcrumbs.vue";

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
  border-radius: 16rem 16rem 0 0;
  padding: 32rem 0 64rem 0;

  &-content{
    width: 70%;
    display: flex;
    flex-direction: column;
    gap: 32rem;

    @media (max-width: 768px) {
      & {
        width: 95%;
      }
    }
  }

  &-header {
    display: flex;
    flex-direction: column;
    gap: 16rem;

    &-tags {
      display: flex;
      flex-direction: row;
      gap: 8rem;
    }

    &-title {
      h1 {
        font-family: Unbounded, sans-serif;
        font-size: 48rem;
        line-height: 56rem;
        color: #423F3F;
      }
    }

    &-date {
      font-weight: 500;
      color: #CFCFCF;

      span {
        border-bottom: 1rem #CFCFCF solid;
        font-size: 16rem;
        line-height: 16rem;
      }
    }
  }
}

</style>