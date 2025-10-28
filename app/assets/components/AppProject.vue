<template>
    <section class="v-app-project"
    >
      <h2 class="v-app-project__title">{{ title }}</h2>
      <div class="v-app-project__content">
        <slot />
      </div>
    </section>
</template>





<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
    title: string
}>()
</script>





<style lang="scss" scoped >
.v-app-project {
  width: 100%;
}

:global(.v-app-project__content img) {
  display: block;
  width: 100%;
  height: auto;
}

</style>
