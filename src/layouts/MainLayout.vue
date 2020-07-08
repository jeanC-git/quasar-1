<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-light-blue-14 glossy text-white">
        <q-btn
          flat
          round
          dense
          icon="menu"
          class="q-mr-sm"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
        <q-avatar>
          <img src="https://somadevoos.com/public_image/favicon.png" />
        </q-avatar>

        <q-toolbar-title>R8vn</q-toolbar-title>

        <q-btn flat round dense icon="whatshot" />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered content-class="bg-grey-1">
      <q-list>
        <q-item-label header class="text-grey-8">Sobre mí</q-item-label>
        <EssentialLink v-for="link in menu" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";

export default {
  name: "MainLayout",

  components: {
    EssentialLink
  },

  data() {
    return {
      leftDrawerOpen: false,
      menu: [
        {
          title: "Fb/r8vn.fb",
          caption: "fb/r8vn.fb",
          icon: "mdi-facebook",
          link: "https://www.facebook.com/r8vn.fb"
        },
        {
          title: "Github/jeanC-git",
          caption: "github.com/jeanC-git",
          icon: "mdi-code-tags",
          link: "https://github.com/jeanC-git"
        },
        {
          title: "SOMA",
          caption: "somadevoos.com",
          icon: "mdi-link-variant",
          link: "https://somadevoos.com"
        }
      ]
    };
  }
};
</script>
