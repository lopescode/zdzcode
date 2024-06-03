<template>
  <v-app id="inspire">
    <Sidebar />

    <v-main>
      <v-container :fluid="true">
        <RouterView />
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import Sidebar from "@/components/Sidebar.vue";
import { RouterView } from "vue-router";
</script>
