<script setup>
import MonBouton from "../components/MonBouton.vue";
import TitreNiv1 from "../components/Titres/TitreNiv1.vue";
import TitreNiv2 from "@/components/Titres/TitreNiv2.vue";
import TitreNiv3 from "@/components/Titres/TitreNiv3.vue";
</script>

<template>
  <main>
    <TitreNiv1>Titre de niveau 1</TitreNiv1>
    <TitreNiv2>Titre de niveau 2</TitreNiv2>
    <TitreNiv3>Titre de niveau 3</TitreNiv3>
    <div class="my-8 flex space-x-5">
      <MonBouton>Clic !</MonBouton>
      <MonBouton type="secondary">Clic !</MonBouton>
      <MonBouton type="danger">Clic !</MonBouton>
      <MonBouton type="danger" isDisabled>Clic !</MonBouton>
    </div>
  </main>
</template>
