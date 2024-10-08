<script setup>
import TitreNiv1 from "@/components/Titres/TitreNiv1.vue";
import flags from "@/assets/flags.json";
import { onBeforeUnmount, onMounted, ref } from "vue";

const pays = ref(flags.countries);
const selected = ref("");
const isOpen = ref(false);
const flagSelector = ref(null);

const selectFlag = (name) => {
  selected.value = name;
  isOpen.value = false;
};

const search = () => {
  pays.value = flags.countries.filter((country) => {
    return country.name
      .toLowerCase()
      .includes(selected.value.toLocaleLowerCase());
  });
};

const clickOutsideHandler = (event) => {
  if (flagSelector.value && !flagSelector.value.contains(event.target)) {
    isOpen.value = false;
  }
};

onMounted(() => {
  document.addEventListener("mousedown", clickOutsideHandler);
});

onBeforeUnmount(() => {
  document.removeEventListener("mousedown", clickOutsideHandler);
});
</script>

<template>
  <div>
    <TitreNiv1>Select de pays et drapeaux</TitreNiv1>

    <div class="relative mt-5 w-56" ref="flagSelector">
      <i
        :class="isOpen ? 'ri-arrow-up-s-line' : 'ri-arrow-down-s-line'"
        class="absolute right-2 top-1/2 transform -translate-y-1/2 text-gray-500 pointer-events-none"
      ></i>

      <input
        placeholder="Selectionnez un pays"
        @focus="isOpen = true"
        @input="search"
        v-model="selected"
        ref="input"
        type="text"
        class="rounded-md shadow-md bg-yellow-50 py-2 px-4 w-full"
      />
      <ul
        v-show="isOpen"
        class="max-h-52 flex flex-col absolute my-2 overflow-y-auto bg-gray-100 rounded-md shadow-md divide-y w-full"
      >
        <li
          class="flex space-x-2 items-center px-4 py-1 cursor-pointer"
          v-for="flag in pays"
          :key="`flag-${flag.code.toLowerCase()}`"
          @click="selectFlag(flag.name)"
        >
          <span :class="`fi fi-${flag.code.toLowerCase()}`"></span>
          <div>{{ flag.name }}</div>
        </li>
        <li
          class="flex space-x-2 items-center px-4 py-1 cursor-pointer"
          v-if="pays.length === 0"
        >
          Pas de résultat pour votre recherche.
        </li>
      </ul>
    </div>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Eos quia similique
    natus laboriosam debitis, iste excepturi quam quibusdam sit eius quaerat
    commodi quae et distinctio voluptas soluta vel! Nemo, distinctio.
  </div>
</template>
