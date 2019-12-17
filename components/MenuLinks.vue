/* eslint-disable */
<template>
  <!-- Links Wrapper -->
  <v-list color="black" :class="listClass">
    <!-- General links -->
    <v-list-item
      v-for="(item, i) in generalLinks"
      :key="i + `-${item.title}`"
      :to="item.to"
      :class="listItemClass + ' px-3'"
      dark
      router
      exact
    >
      <v-list-item-action class="mr-1">
        <v-icon>{{ item.icon }}</v-icon>
      </v-list-item-action>
      <v-list-item-content>
        <v-list-item-title v-text="item.title" />
      </v-list-item-content>
    </v-list-item>
  </v-list>
</template>

<script>
import { mapActions, mapState } from 'vuex';

export default {
  name: 'MenuLinks',
  props: {
    generalLinks: {
      type: Array,
      default() {
        return [];
      }
    },
    listClass: {
      type: String,
      default: ''
    },
    listItemClass: {
      type: String,
      default: ''
    }
  }
};
</script>

<style>
</style>
