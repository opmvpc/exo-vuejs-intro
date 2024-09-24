<script setup>
import MonBouton from "../components/MonBouton.vue"
import TitreNiv1 from "../components/Titres/TitreNiv1.vue"
</script>

<template>
  <main>
    <TitreNiv1>Hello ! Comment ça va??</TitreNiv1>
    <div class="my-8 flex space-x-5">
      <MonBouton>Clic !</MonBouton>
      <MonBouton type="secondary">Clic !</MonBouton>
      <MonBouton type="danger">Clic !</MonBouton>
      <MonBouton type="danger" isDisabled>Clic !</MonBouton>
    </div>
  </main>
</template>
