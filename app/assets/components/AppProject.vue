<template>
    <section class="v-app-project"
             :class="{ 'v-app-project--has-toggle': has_toggle }"
    >
      <div class="v-app-project__aside">
        <img class="v-app-project__cover"
             v-if="cover"
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
        <img class="v-app-project__content__cover"
             v-if="cover"
             :src="cover"
             :alt="`image de couverture de ${title}`"
        >

        <template v-if="isOpen && has_toggle">
          <slot/>
        </template>
        <template v-else-if="!has_toggle">
          <slot/>
        </template>

        <button class="v-app-project__content__toggle"
                @click="isOpen = !isOpen"
                v-if="has_toggle"
        >
          <svg v-if="isOpen"
               xmlns="http://www.w3.org/2000/svg"
               height="24px" viewBox="0 -960 960 960" width="24px" fill="#e3e3e3"><path d="M200-440v-80h560v80H200Z"/></svg>
          <svg v-else
               xmlns="http://www.w3.org/2000/svg"
               height="24px" viewBox="0 -960 960 960" width="24px" fill="#e3e3e3"><path d="M440-120v-320H120v-80h320v-320h80v320h320v80H520v320h-80Z"/></svg>
        </button>
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

const isOpen = ref(false)

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
  position: sticky;
  top: 1rem;
  border: solid 2px #109d34;
  margin-top: 1rem;
}

.v-app-project__content {
  width: calc( ((100% + var(--gutter)) / 12 * 8) - var(--gutter));
  max-width: 40rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  @media (max-width: 1000px) {
    width: calc( ((100% + var(--gutter)) / 12 * 12) - var(--gutter));
  }
}

.v-app-project__content__cover {
  display: block;
  height: auto;
  width: 100%;
  object-fit: contain;
  object-position: left;
  margin-bottom: 1rem;
  border: solid 2px #109d34;
}

.v-app-project__content__toggle {
  all: unset;
  cursor: pointer;
  display: flex;
  width: 100%;
  justify-content: flex-end;
  margin-bottom: 1rem;

  svg {
    fill: #109d34;
    height: 2rem;
    width: auto;
  }
}



/**
images cover
 */
.v-app-project__cover {
    display: none;
  @media (max-width: 1000px) {
  display: block;
  }
}
.v-app-project__content__cover {
    display: block;
  @media (max-width: 1000px) {
  display: none;
  }
}
.v-app-project--has-toggle {
  .v-app-project__cover {
      display: block;
    @media (max-width: 1000px) {
    display: none;
    }
  }

  .v-app-project__content__cover {
      display: none;
    @media (max-width: 1000px) {
    display: block;
    }
  }
}

</style>
