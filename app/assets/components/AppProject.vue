<template>
    <section class="v-app-project"
             :class="{ 'v-app-project--has-toggle': has_toggle }"
    >
      <div class="v-app-project__aside">
        <img class="v-app-project__cover"
             v-if="cover && has_toggle"
             :src="cover"
             :alt="`image de couverture de ${title}`"
        >
      </div>
      <div class="v-app-project__content">
        <h2 class="v-app-project__content__title"
        >
          <span v-if="info" style="font-weight: normal">{{ info }}</span>
          {{ title }}
          <span v-if="type" style="font-weight: normal">— {{ type }}</span>
        </h2>
        <img class="v-app-project__cover"
             v-if="cover && !has_toggle"
             :src="cover"
             :alt="`image de couverture de ${title}`"
        >
        <slot/>
      </div>
    </section>
</template>





<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
  title: string
  info?: string
  type?: string
  has_toggle?: boolean
  cover?: string
}>()
</script>





<style lang="scss" scoped >
.v-app-project {
  width: 100%;
  color: #109d34;
  border-top: solid 2px #109d34;
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;

  --gutter: 1rem;
}

.v-app-project__aside {
  width: calc( ((100% + var(--gutter)) / 12 * 4) - var(--gutter));

    @media (max-width: 1000px) {
      width: calc( ((100% + var(--gutter)) / 12 * 12) - var(--gutter));
    }
}

.v-app-project__cover {
  display: block;
  height: auto;
  width: 100%;
  max-height: 95vh;
  object-fit: contain;
  object-position: left;
  margin-bottom: 1rem;

  .v-app-project--has-toggle & {
    position: sticky;
    top: 1rem;
    border: solid 2px #109d34;
    margin-top: 1rem;
    max-height: none;
  }
}

.v-app-project__content {
  width: calc( ((100% + var(--gutter)) / 12 * 8) - var(--gutter));
  max-width: 40rem;

  @media (max-width: 1000px) {
    width: calc( ((100% + var(--gutter)) / 12 * 12) - var(--gutter));
  }
}

</style>
