<template>
  <section class="r-section">
    <RDivider class="mb-2" />
    <div class="section-wrapper">
      <h2 class="section__title">
        {{ metaData.title ?? '[SECTION TITLE]' }}
      </h2>
      <div class="section__content">
        <article
          v-for="(subContent, subIndex) in metaData.contents"
          :key="subIndex"
          class="section__sub-content"
        >
          <div v-if="subContent.timeline" class="section-content__timeline">
            <span :class="['timeline__date', subContent.timeline?.className ?? '']">
              {{ subContent.timeline?.start }} - {{ subContent.timeline?.end ?? '' }}
            </span>
            <strong class="timeline__title">
              {{ subContent.timeline?.subTitle }}
            </strong>
            <span class="timeline__end">
              {{ subContent.timeline?.endText }}
            </span>
          </div>
          <VueMarkdown v-model="subContent.content" />
        </article>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import RDivider from './r-divider.vue';
import VueMarkdown from 'vue-markdown-wasm';
interface RSectionProp {
  data: {
    title: string;
    contents: {
      content: string;
      timeline?: {
        start: string;
        end?: string;
        className?: string;
        subTitle: string;
        endText?: string;
      };
    }[];
  };
}
const props = withDefaults(defineProps<RSectionProp>(), {
  data: () => ({
    title: '',
    contents: []
  })
});
const metaData = computed(() => props.data);
</script>

<style scoped>
@reference "../style.css";
.section-wrapper {
  @apply flex flex-col md:flex-row w-full gap-4;
}
.section__title {
  @apply text-base font-semibold md:w-32 text-left shrink-0 ms-1 md:ms-3;
}
.section-content__timeline {
  @apply flex text-nowrap flex-wrap items-center justify-center md:justify-start gap-2 mb-2;

  .timeline__date {
    @apply min-w-32 indent-0 my-2 w-fit inline-flex items-center px-3 rounded-lg font-medium;
  }

  .timeline__title {
    @apply text-sm md:text-base text-center flex-1;
  }

  .timeline__end {
    @apply text-xs md:text-sm text-blue-800 font-semibold;
  }
}

.section__content {
  --content-width: calc(100% - (var(--spacing) * 40));
  @apply flex-1 !text-wrap text-sm;
}
:deep(.section__content .vue-markdown) {
  @apply !text-wrap;
}
:deep(.section__content .vue-markdown p) {
  @apply !text-wrap mb-2 md:ps-6 indent-8 text-left;
}
:deep(.section__content .vue-markdown ul) {
  @apply !list-disc mb-2 ms-12  flex flex-col gap-1.5 text-sm/5;
}
:deep(.section__content .vue-markdown a) {
  @apply text-blue-500 indent-0 decoration-1 decoration-sky-500;
}

:deep(.section__content .vue-markdown blockquote) {
  @apply !text-wrap mb-2 me-2  text-text-blockquote font-medium text-xs;

  font-family: 'Source Han Serif SC', serif;
  p{
    @apply indent-0 ps-0;
  }
}

:deep(.section__content .vue-markdown pre) {
  @apply !text-wrap mb-2 rounded-lg bg-gray-100 p-4 text-xs overflow-x-auto;
  code{
    @apply !text-left indent-0;
  }
}
</style>
