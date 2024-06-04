<template>
  <v-app>
    <v-main>
      <v-btn @click="toggleTheme"><v-icon>mdi-theme-light-dark</v-icon></v-btn>
      <router-view />
    </v-main>
  </v-app>
</template>

<script setup>
import { useTheme } from 'vuetify'

const theme = useTheme()

function toggleTheme () {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
}
</script>
