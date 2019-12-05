<template>
  <v-app class="white">
    <!-- Header Area -->
    <v-app-bar
      app
      color="black"
      elevate-on-scroll
      fixed
      hide-on-scroll
      scroll-threshold="100"
      prominent
      height="70px"
    >
      <v-toolbar-title class="headline d-flex justify-center align-center align-self-center">
        <v-img
          class="align-center"
          alt="logo description"
          src="/images/weirwood-media-logo.svg"
          lazy-src="/images/weirwood-media-logo.svg"
          height="45px"
          width="55px"
        />
        <p class="white--text ma-0 pl-2">Weirwood Media</p>
      </v-toolbar-title>
      <v-spacer />
      <v-app-bar-nav-icon color="white" class="hidden-md-and-up" @click.stop="drawer = !drawer" />
      <!-- tablet/desktop header navigation -->
      <MenuLinks
        :general-links="generalLinks"
        list-class="row hidden-md-and-down"
        list-item-class="row-menu"
      />
    </v-app-bar>
    <!-- side/mobile navigation -->
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      class="primary"
      fixed
      dark
      app
      right
    >
      <MenuLinks :general-links="generalLinks" list-class="listClass" list-item-class="column" />
    </v-navigation-drawer>
    <!-- Nuxt content -->
    <v-content>
      <nuxt />
    </v-content>
    <!-- Footer Area -->
    <v-footer color="secondary darken-2" class="pa-0">
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="(link, i) in footerLinks"
          :key="i + link.title"
          color="white"
          text
          rounded
          nuxt
          :to="link.to"
          class="my-2"
        >{{ link.title }}</v-btn>
        <v-col class="primary py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} —
          <strong>Weirwood Media</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
import MenuLinks from '../components/MenuLinks.vue';

export default {
  components: {
    MenuLinks
  },
  data() {
    return {
      drawer: false,
      fixed: false,
      footerLinks: [
        {
          title: 'Home',
          to: '/'
        },
        {
          title: 'Services',
          to: '/services'
        },
        {
          title: 'Portfolio',
          to: '/portfolio'
        },
        {
          title: 'Blog',
          to: '/blog'
        },
        {
          title: 'About Us',
          to: '/about'
        },
        {
          title: 'Contact ',
          to: '/contact'
        }
      ],
      generalLinks: [
        {
          icon: 'mdi-apps',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-toolbox-outline',
          title: 'Services',
          to: '/services'
        },
        {
          icon: 'mdi-folder-multiple',
          title: 'Portfolio',
          to: '/portfolio'
        },
        {
          icon: 'mdi-post',
          title: 'Blog',
          to: '/blog'
        },
        {
          icon: 'mdi-account-supervisor',
          title: 'About',
          to: '/about'
        },
        {
          icon: 'mdi-email-send',
          title: 'Contact',
          to: '/contact'
        }
      ],
      miniVariant: false,
      title: 'Company Name'
    };
  }
};
</script>

<style lang="scss">
</style>