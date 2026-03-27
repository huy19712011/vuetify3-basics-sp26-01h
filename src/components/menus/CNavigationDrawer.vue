<template>
  <v-navigation-drawer permanent>
    <v-list nav density="compact">
      <!-- Simple item -->
      <v-list-item
        prepend-icon="mdi-home"
        title="Dashboard"
        value="dashboard"
        to="/dashboard"
      />
      <v-list-item
        prepend-icon="mdi-list-box-outline"
        title="Product List"
        value="productList"
        to="/products"
      />

      <!-- Nested group -->
      <v-list-group value="Settings">
        <template #activator="{ props }">
          <v-list-item v-bind="props" prepend-icon="mdi-cog" title="Settings" />
        </template>

        <!-- Children — level 1 -->
        <v-list-item
          title="Profile"
          value="profile"
          to="/profile"
          prepend-icon="mdi-face-man-profile"
        />
        <v-list-item
          title="Security"
          value="security"
          to="/security"
          prepend-icon="mdi-security"
        />

        <!-- Double-nested group — level 1 activator -->
        <v-list-group value="Notifications">
          <template #activator="{ props }">
            <v-list-item
              v-bind="props"
              title="Notifications"
              prepend-icon="mdi-bell-outline"
            />
          </template>

          <!-- Triple-nested group — level 2 activator -->
          <v-list-group value="Email">
            <template #activator="{ props }">
              <v-list-item
                v-bind="props"
                title="Email"
                prepend-icon="mdi-email-box"
              />
            </template>

            <!-- Children — level 3 -->
            <v-list-item title="Work" value="work" prepend-icon="mdi-email" />
            <v-list-item
              title="Personal"
              value="personal"
              prepend-icon="mdi-email"
            />
          </v-list-group>

          <!-- Children — level 2 -->
          <v-list-item
            title="SMS"
            value="sms"
            prepend-icon="mdi-message-outline"
          />
        </v-list-group>
      </v-list-group>
    </v-list>
  </v-navigation-drawer>
</template>

<style scoped>
/* Level 1 children: Profile, Security, Notifications activator */
:deep(.v-list-group__items > .v-list-item),
:deep(.v-list-group__items > .v-list-group > .v-list-group__header) {
  padding-inline-start: 40px !important;
}

/* Level 2 children: Email activator, SMS */
:deep(
  .v-list-group__items > .v-list-group > .v-list-group__items > .v-list-item
),
:deep(
  .v-list-group__items
    > .v-list-group
    > .v-list-group__items
    > .v-list-group
    > .v-list-group__header
) {
  padding-inline-start: 64px !important;
}

/* Level 3 children: Work, Personal */
:deep(
  .v-list-group__items
    > .v-list-group
    > .v-list-group__items
    > .v-list-group
    > .v-list-group__items
    > .v-list-item
) {
  padding-inline-start: 88px !important;
}
</style>
