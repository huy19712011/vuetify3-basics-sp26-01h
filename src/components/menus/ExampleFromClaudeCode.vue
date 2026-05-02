<template>
  <v-navigation-drawer app permanent width="250">
    <!-- Root level list -->
    <v-list dense nav>
      <v-list-item>
        <v-list-item-title>Home</v-list-item-title>
      </v-list-item>

      <!-- First nested group -->
      <v-list-group
        prepend-icon="mdi-folder"
        value="projects"
        v-model:opened="openedGroups"
      >
        <template v-slot:activator="{ props }">
          <v-list-item v-bind="props">
            <v-list-item-title>Projects</v-list-item-title>
          </v-list-item>
        </template>

        <v-list-item>
          <v-list-item-title>Project A</v-list-item-title>
        </v-list-item>
        <v-list-item>
          <v-list-item-title>Project B</v-list-item-title>
        </v-list-item>

        <!-- Second nested group inside first group -->
        <v-list-group
          prepend-icon="mdi-folder"
          value="subprojects"
          v-model:opened="openedGroups"
        >
          <template v-slot:activator="{ props }">
            <v-list-item v-bind="props">
              <v-list-item-title>Sub Projects</v-list-item-title>
            </v-list-item>
          </template>

          <v-list-item>
            <v-list-item-title>Sub‑A</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Sub‑B</v-list-item-title>
          </v-list-item>
        </v-list-group>
      </v-list-group>

      <!-- Second root level group -->
      <v-list-group
        prepend-icon="mdi-account"
        value="users"
        v-model:opened="openedGroups"
      >
        <template v-slot:activator="{ props }">
          <v-list-item v-bind="props">
            <v-list-item-title>Users</v-list-item-title>
          </v-list-item>
        </template>

        <v-list-item>
          <v-list-item-title>Admin</v-list-item-title>
        </v-list-item>
        <v-list-item>
          <v-list-item-title>Editor</v-list-item-title>
        </v-list-item>
      </v-list-group>
    </v-list>
  </v-navigation-drawer>
</template>

<script setup>
import { ref } from "vue";

const openedGroups = ref(["projects", "users"]); // Start with Projects and Users expanded
</script>

<style scoped>
/* Optional styling tweaks */
</style>
