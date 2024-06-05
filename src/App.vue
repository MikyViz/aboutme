<template>
  <v-app>
    <v-main>
      <RouterLink to="/ProfScils">Home</RouterLink>
      <!-- <v-card>
          <v-layout>
            <v-app-bar color="primary" prominent>
              <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

              <v-toolbar-title>My files</v-toolbar-title>

              <v-spacer></v-spacer>

              <template v-if="$vuetify.display.mdAndUp">
                <v-btn icon="mdi-magnify" variant="text"></v-btn>

                <v-btn icon="mdi-filter" variant="text"></v-btn>
              </template>

<v-btn icon="mdi-dots-vertical" variant="text"></v-btn>
</v-app-bar>

<v-navigation-drawer v-model="drawer" :location="$vuetify.display.mobile ? 'bottom' : undefined" temporary>
  <v-list :items="items"></v-list>
</v-navigation-drawer>

<v-main style="height: 500px;">
  <v-card-text>
    The navigation drawer will appear from the bottom on smaller size screens.
  </v-card-text>
</v-main>
</v-layout>
</v-card> -->
      <v-app-bar color="indigo" prominent="true">
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>About Miky Viz 🫎</v-toolbar-title>
        <v-spacer></v-spacer>
        <template v-if="$vuetify.display.mdAndUp">
          <v-btn icon="mdi-magnify" variant="text"></v-btn>
          <v-btn icon="mdi-filter" variant="text"></v-btn>
        </template>
        <v-btn @click="toggleTheme"><v-icon>mdi-theme-light-dark</v-icon></v-btn>
        <v-btn icon="mdi-dots-vertical" variant="text"></v-btn>
      </v-app-bar>
      <v-navigation-drawer v-model="drawer" :location="$vuetify.display.mobile ? 'bottom' : undefined" temporary>
        <v-list :items="items"></v-list>
      </v-navigation-drawer>
      <router-view />
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, watch } from 'vue'
// import { useRouter } from 'vue-router'
import { useTheme } from 'vuetify'
import router from './router';

// router = useRouter();

let drawer = ref(null);
drawer.value = false;
let group = ref(null);
const items = ref([]);
items.value = [
  {
    title: 'Foo',
    value: ()=>router.push('/ProfScils'),
  },
  {
    title: 'Bar',
    value: 'bar',
  },
  {
    title: 'Fizz',
    value: 'fizz',
  },
  {
    title: 'Buzz',
    value: 'buzz',
  },
],

  watch(() => group, () => {
    drawer.value = false
  }
  )
const theme = useTheme()

function toggleTheme() {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
}
</script>

<style scoped></style>
