<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-primary text-dark" height-hint="98">
      <q-toolbar class="header__border">
        <q-toolbar-title class="flex flex-center text-dark">
          Nayan's Note - {{ title }}
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
    <q-footer bordered class="bg-primary text-dark">
      <q-tabs align="center">
        <q-route-tab to="/" label="Add Sell" />
        <q-route-tab to="/list" label="List Sell" />
      </q-tabs>
    </q-footer>
  </q-layout>
</template>

<script>
import { openURL } from "quasar";
export default {
  data() {
    return {};
  },
  computed: {
    title() {
      let currentPath = this.$route.fullPath;
      if (currentPath == "/") {
        return "Home";
      } else {
        return "List View";
      }
    }
  },
  methods: {
    openURL
  }
};
</script>
<style scoped></style>
