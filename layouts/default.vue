<script setup lang="ts">
import { useTheme } from "vuetify";

const theme = useTheme();
const darkTheme = ref(false);
const order = ref(0);

import {
  mdiArrowExpandVertical,
  mdiAccount,
  mdiMouse,
  mdiKeyboard,
} from "@mdi/js";

const changeTheme = () => {
  theme.global.name.value = darkTheme.value ? "mainDarkTheme" : "mainTheme";
};
</script>

<template>
  <v-layout class="rounded rounded-md">
    <v-navigation-drawer color="primary" permanent>
      <v-list density="compact" nav>
        <v-list-item :prepend-icon="mdiArrowExpandVertical">
          <v-switch
            v-model="order"
            hide-details
            inset
            true-value="-1"
            false-value="0"
          ></v-switch>
        </v-list-item>
        <v-list-item
          :prepend-icon="mdiAccount"
          title="Profile"
          value="Profile"
        ></v-list-item>
        <v-list-item
          :prepend-icon="mdiMouse"
          title="Mouse"
          value="Mouse"
        ></v-list-item>
        <v-list-item
          :prepend-icon="mdiKeyboard"
          title="Keyboard"
          value="Keyboard"
        ></v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :order="order" title="Nuxt3 Vutify3">
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
  </v-layout>
</template>
