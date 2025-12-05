<script setup lang="ts">
import { computed } from 'vue';
import type { KeyValuePair } from '../model';

interface RHeaderProp {
  data: {
    avatar: string;
    name: string;
    secondName: string;
    misc: KeyValuePair[];
    position?: string;
  };
}
const props = defineProps<RHeaderProp>();

const metaData = computed(() => props.data);

// TODO: it should be localized or configurable
const _PROFILE_FIRST_KEY = 'POSITION';

const avatar = computed(() => {
  return metaData.value.avatar ?? 'https://via.placeholder.com/100x140?text=AVATAR';
});
</script>

<template>
  <header class="r-header">
    <div class="header-wrapper">
      <div class="avatar-section">
        <img class="avatar-1inch" :src="avatar" alt="AVATAR" />
      </div>
      <div class="name-section">
        <div class="name">{{ metaData.name ?? '[YOUR_NAME]' }}</div>
        <div class="second-name">{{ metaData.secondName ?? '' }}</div>
      </div>
      <ul class="profile-property-section">
        <li class="profile-property-line items-center">
          <span class="profile-property-line__key">{{ _PROFILE_FIRST_KEY }}</span>
          <strong class="profile-property-line__value !text-base md:!text-lg">
            {{ metaData.position ?? '[POSITION]' }}
          </strong>
        </li>
        <li v-for="item in metaData.misc" :key="item.key" class="profile-property-line">
          <span class="profile-property-line__key">
            {{ item.key }}
          </span>
          <span class="profile-property-line__value">{{ item.value }}</span>
        </li>
      </ul>
    </div>
  </header>
</template>

<style scoped>
@reference "../style.css";
.r-header {
  @apply bg-header min-h-48 border-b border-b-line;
  .header-wrapper {
    @apply flex px-6 py-6 h-full justify-between w-full gap-6;
  }
}
.avatar-section {
  @apply flex flex-col justify-center shrink-0;
  .avatar-1inch {
    @apply w-[100px] h-[140px];
  }
}
.name-section {
  @apply flex flex-col justify-center gap-2 flex-1;

  .name {
    @apply text-lg md:text-3xl font-bold text-nowrap whitespace-break-spaces;
  }
  .second-name {
    @apply text-sm font-bold md:text-base;
  }
}
.profile-property-section {
  @apply flex flex-col gap-2 justify-center;
}
.profile-property-line {
  @apply flex flex-row gap-2 flex-wrap;
}
.profile-property-line__value {
  @apply text-xs md:text-sm text-nowrap;
}
.profile-property-line__key {
  @apply text-xs md:text-sm text-center min-w-16 px-1 bg-slate-800 text-white;
  &.position {
    @apply text-center min-w-24 px-1 bg-slate-800 text-white h-fit;
  }
}
</style>
