<template>
  <div class="v-index"
  >
    <header class="v-index__header">
      <img class="v-index__header__logo" src="/img.png" alt="logo" />
    </header>
    <main class="v-index__main">
      <h1 class="v-index__main__title">Résidence COLECTIVA</h1>

      <div class="v-index__main__projects">
        <AppProject title="Association Nébuleuse">
          <p>COLECTIVA est un programme de résidences orienté vers les domaines des arts visuels et sonores qui a débuté
            en 2022.</p>
          <p>COLECTIVA s’engage dans des réflexions sur la vie en communauté et a pour but de créer des liens entre les
            différentes structures culturelles du canton de Genève. COLECTIVA veut aussi visibiliser des artistes
            travaillant en Amérique Latine et les mettre en lien avec la Suisse pour stimuler les échanges culturels entre
            ces deux espaces.</p>
          <img src="/images/projects/association_nebuleuse/img.png" alt="image du couverture" />
        </AppProject>
      </div>

    </main>
  </div>
</template>


<style lang="scss" scoped>
.v-index {
  padding: 2rem;
}

.v-index__header {
  display: flex;
  align-items: center;
  justify-content: center;
}

.v-index__header__logo {
  height: 1rem;
}

.v-index__main {
  max-width: 40rem;
  margin-left: auto;
  margin-right: auto;
}

.v-index__main__projects {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
<script setup lang="ts">
import AppProject from "~/assets/components/AppProject.vue";
</script>
