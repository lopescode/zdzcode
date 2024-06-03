<template>
  <v-navigation-drawer class="pt-4" color="grey-lighten-3" model-value rail>
    <v-avatar
      key="avatar"
      color="grey-darken-1"
      size="36"
      class="d-block text-center mx-auto mb-9"
    ></v-avatar>

    <v-avatar
      v-for="n in 2"
      :key="n"
      color="grey-lighten-1"
      size="20"
      class="d-block text-center mx-auto mb-9"
    ></v-avatar>
  </v-navigation-drawer>
</template>
