<template>
  <v-app>
    <v-navigation-drawer
      app
      temporary
      v-model="sideNavigation">
      <v-list dense>
        <v-subheader>ACTIONS</v-subheader>
        <v-list-item-group>
          <v-list-item
            v-for="menuItem in menuItems"
            :key="menuItem.title">
            <v-list-item-icon>
              <v-icon>{{ menuItem.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>
                <router-link :to="menuItem.link">{{ menuItem.title }}</router-link>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
      <v-toolbar
        class="primary"
        height="40px">
        <v-app-bar-nav-icon
          @click.native.stop="sideNavigation = !sideNavigation"
          class="hidden-sm-and-up"
        ></v-app-bar-nav-icon>
        <v-toolbar-title>
          <router-link to="/">DevMeetUp</router-link>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-xs-only">
          <v-btn
            plain
            v-for="menuItem in menuItems"
            :key="menuItem.title">
            <v-icon left>{{ menuItem.icon }}</v-icon>
            <router-link :to="menuItem.link">{{ menuItem.title }}</router-link>
          </v-btn>
        </v-toolbar-items>
      </v-toolbar>
    <main>
      <router-view></router-view>
    </main>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    sideNavigation: false,
    menuItems: [
      { icon: 'mdi-account-multiple', title: 'View Meetups', link: '/meetups/all' },
      { icon: 'mdi-map-marker', title: 'Organize meetup', link: '/meetups/new' },
      { icon: 'mdi-account', title: 'Profile', link: '/profile' },
      { icon: 'mdi-lock-open-outline', title: 'Sign in', link: '/signin' },
      { icon: 'mdi-face-man', title: 'Sign up', link: '/signup' }
    ]
  })
}
</script>
