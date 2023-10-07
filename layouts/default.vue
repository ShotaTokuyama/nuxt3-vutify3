<script setup lang="ts">
import { useTheme } from "vuetify";

const darkTheme = ref(false);
const theme = useTheme();

const changeTheme = () => {
  theme.global.name.value = darkTheme.value ? "mainDarkTheme" : "mainTheme";
};
</script>

<template>
  <v-app-bar>
    <v-app-bar-title> Nuxt3 Vutify3 </v-app-bar-title>
    <template v-slot:append>
      <v-switch
        v-model="darkTheme"
        @update:model-value="changeTheme"
        hide-details
        inset
        class="mr-auto"
      />
    </template>
  </v-app-bar>
  <v-main><slot /></v-main>
</template>
