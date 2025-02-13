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
          ></Tag>
        </div>
        <div class="news-popup-header-title">
          <h1>{{ news.data.result.title }}</h1>
        </div>
        <div class="news-popup-header-date">
          <span>{{ news.data.result.date.replaceAll('-', '.') }}</span>

        </div>
      </div>
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
  border-radius: 16px 16px 0 0;
  padding: 32px 0 64px 0;

  &-content{
    width: 70%;
    display: flex;
    flex-direction: column;
  }

  &-header {
    display: flex;
    flex-direction: column;
    gap: 16px;

    &-tags {
      display: flex;
      flex-direction: row;
      gap: 8px;
    }

    &-title {
      margin-bottom: 16px;
      h1 {
        font-family: Unbounded, sans-serif;
        font-size: 48px;
        line-height: 56px;
        color: #423F3F;
      }
    }

    &-date {
      font-weight: 500;
      font-size: 16px;
      line-height: 16px;
      color: #CFCFCF;

      span {
        border-bottom: 1px #CFCFCF solid;
      }
    }
  }
}

</style>