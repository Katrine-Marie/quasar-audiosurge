
<template>
<q-layout view="lHh Lpr lFf">
  <q-header elevated>
    <q-toolbar>
      <q-toolbar-title>
        Quasar Audiosurge
      </q-toolbar-title>

      <q-btn color="white" text-color="primary">
        Load File
        <input
          type="file"
          class="q-uploader__input overflow-hidden absolute-full"
          v-on:change="fileChosen"
          ref="fileInput"
          accept="audio/mpeg"
        />
      </q-btn>
    </q-toolbar>
  </q-header>

  <q-page-container>
    <router-view />
  </q-page-container>
</q-layout>
</template>

<script>
import { openURL } from 'quasar'
import { EventBus } from '../services/event-bus.js'
export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop
    }
  },
  methods: {
    openURL,
    fileChosen (file) {
      EventBus.$emit('fileChosen', file)
    }
  }
}
</script>

<style>
</style>
