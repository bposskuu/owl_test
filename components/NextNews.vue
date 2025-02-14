<template>
  <div class="next-news">
    <h1>Следующая статья</h1>
      <div class="next-news-content" @click="pushToNextNews">
        <div class="next-news-content-picture">
          <div class="next-news-content-picture-date">
            {{ nextNews.date.replaceAll('-', '.') }}
          </div>
          <div class="next-news-content-picture-img">
            <img :src="nextNews.picture" alt="">
          </div>
        </div>
        <div class="next-news-content-info">
          <h2>{{ nextNews.title }}</h2>

          <div class="next-news-content-info-tags">
            <Tag
                v-for="(tag, i) in nextNews.tags"
                :key="i"
                :tag="tag"
            />
          </div>
        </div>
        <div class="next-news-content-arrow">
          <img src="~/assets/img/arrow.svg" alt="">
        </div>
    </div>

  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  nextNews: {
    type: Object,
    required: true
  },
})

const router = useRouter()

const pushToNextNews = () => {
  router.push('/news/' + props.nextNews.code)
}

</script>

<style scoped lang="scss">
.next-news {
  display: flex;
  gap: 32rem;
  flex-direction: column;


  h1 {
    font-size: 40rem;
    font-family: Unbounded, sans-serif;
    color: #423F3F;
    line-height: 48rem;
  }

  &-content {
    cursor: pointer;
    position: relative;
    display: flex;
    flex-direction: row;
    border-radius: 26rem;
    gap: 24rem;
    background: url('~/assets/img/mask-news.svg');
    background-size: 100% 100%;
    width: 100%;
    height: 228rem;

    @media (max-width: 768px) {
      & {
        background: #f3f3f3;
        height: 100%;
        flex-direction: column;
      }
    }

    &-picture {
      padding: 4rem;
      position: relative;

      @media (max-width: 768px) {
        & {
          padding: 8rem;
          height: 100%;
        }
      }

      &-img {
        width: 320rem;
        border-radius: 24rem;
        overflow: hidden;
        height: 100%;

        @media (max-width: 768px) {
          & {
            width: 100%;
            height: 100%;
          }
        }

        img {
          object-fit: cover;
          height: 100%;
          width: 100%;
        }
      }

      &-date {
        position: absolute;
        top: 16rem;
        left: 16rem;
        background-color: #5B4481;
        opacity: 80%;
        font-size: 14rem;
        line-height: 14rem;
        color: white;
        padding: 8rem 16rem;
        border-radius: 16rem;

        @media (max-width: 768px) {
          & {
            font-size: 24rem;
            padding: 16rem 32rem;
            border-radius: 24rem;
            letter-spacing: .96rem;
            line-height: 24rem;
            left: 32rem;
            top: 32rem;
          }
        }
      }
    }

    &-info {
      display: grid;
      padding: 16rem 24rem 16rem 0;
      width: 600rem;

      @media (max-width: 768px) {
        & {
          width: 90%;
          padding: 16rem;
          gap: 32rem;
        }
      }

      h2 {
        font-size: 24rem;
        line-height: 32rem;
        font-weight: 700;
        color: #423F3F;
        font-family: Unbounded, sans-serif;
      }

      &-tags {
        display: flex;
        flex-direction: row;
        align-self: flex-end;
        gap: 8rem;

        @media (max-width: 768px) {
          & {
            gap: 16rem;
          }
        }
      }
    }

    &-arrow {
      position: absolute;
      top: 0;
      right: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 80rem;
      height: 80rem;
      border-radius: 24rem;
      background-color: white;
      box-shadow: 0 4rem 12rem #1E1A230D, 0 2rem 6rem #5912731A;

      img {
        width: 40rem;
      }

      @media (max-width: 768px) {
        & {
          bottom: 0;
          top: auto;
        }
      }
    }
  }
}
</style>