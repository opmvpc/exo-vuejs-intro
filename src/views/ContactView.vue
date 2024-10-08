<script setup>
import MonBouton from "@/components/MonBouton.vue";
import TitreNiv1 from "@/components/Titres/TitreNiv1.vue";
import { ref } from "vue";

const contactData = ref({
  name: "",
  email: "",
  message: "",
});

const estEnvoye = ref(false);

const envoyer = () => {
  estEnvoye.value = true;
};
</script>

<template>
  <div>
    <TitreNiv1>Contact</TitreNiv1>

    <form class="space-y-4" @submit.prevent="envoyer">
      <div class="flex flex-col space-y-2">
        <label for="name">Nom</label>
        <input
          class="rounded-md shadow-md bg-yellow-50 py-2 px-4"
          id="name"
          type="text"
          v-model="contactData.name"
        />
      </div>

      <div class="flex flex-col space-y-2">
        <label for="email">Email</label>
        <input
          class="rounded-md shadow-md bg-yellow-50 py-2 px-4"
          id="email"
          type="email"
          v-model="contactData.email"
        />
      </div>

      <div class="flex flex-col space-y-2">
        <label for="message">Message</label>
        <textarea
          class="rounded-md shadow-md bg-yellow-50 py-2 px-4"
          v-model="contactData.message"
          placeholder="Votre message..."
        ></textarea>
      </div>
      <MonBouton>Envoyer</MonBouton>
    </form>

    <div v-if="estEnvoye === true">
      <hr class="my-5" />
      <dl>
        <dt>Nom :</dt>
        <dd>{{ contactData.name }}</dd>
        <dt>Email :</dt>
        <dd>{{ contactData.email }}</dd>
        <dt>Message :</dt>
        <dd>{{ contactData.message }}</dd>
      </dl>
    </div>
  </div>
</template>
