<template>
  <q-layout view="hHh Lpr lff">
    <q-header dense elevated>
      <q-toolbar>
        <!-- *** IKONA **** -->
        <!--<q-icon class="q-ma-xs" :key="getIconSize" :size="getIconSize" name="label"/>-->
        <img style="height:35px; width:35px;" src="data:image/png;base64,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">
        <!-- *** TYTUL *** -->
        <q-toolbar-title class="absolute-center">
          ZABAWA W ŚNIEŻKI
        </q-toolbar-title>
        <q-space />
        <!--
        <div>
          {{ appVersion ? 'v.' : '' }}{{ appVersion }} {{ deploymentEnv }}
        </div>
        -->
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="drawer"
      bordered
      content-class="bg-grey-1"
      :width="250"
      :breakpoint="500"
    >
      <q-list class="q-pa-sm">
        <q-item
          to="/"
          clickable
          exact
        >
          <q-item-section>
            <q-icon name="anchor" :key="getIconSize" :size="getIconSize" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{homeTitle}}</q-item-label>
          </q-item-section>
        </q-item>

        <q-item
          clickable
          to="/calcpage"
          exact
        >
          <q-item-section>
            <q-icon name="calculate" :key="getIconSize" :size="getIconSize" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{calcTitle}}</q-item-label>
          </q-item-section>
        </q-item>

                <q-item
          clickable
          to="/rectangle"
          exact
        >
          <q-item-section>
            <q-icon name="highlight_alt" :key="getIconSize" :size="getIconSize" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{rectangleTitle}}</q-item-label>
          </q-item-section>
        </q-item>

                        <q-item
          clickable
          to="/components"
          exact
        >
          <q-item-section>
            <q-icon name="code" :key="getIconSize" :size="getIconSize" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{componentsTitle}}</q-item-label>
          </q-item-section>
        </q-item>

        <q-separator/>

        <q-item>
          <div>
            <canvas id="xxx" width="200" height="4000"></canvas>
          </div>
        </q-item>
      </q-list>
    </q-drawer>
    <q-page-container style="width: 100%; height: 100%;">

      <q-banner class="q-mt-xs bg-primary text-white" dense>
               {{this.titleBanner}}
      </q-banner>
      <router-view />
    </q-page-container>
  </q-layout>
</template>
<script>
import { mapGetters } from 'vuex'
// import Vue from 'vue'

export default {
  name: 'Layout',

  data () {
    return {
      // appVersion: Vue.prototype.$version,
      // deploymentEnv: Vue.prototype.$deploymentEnv === 'test' ? 'TEST' : '',
      drawer: true,
      homeTitle: 'Pierdoły...',
      helpTitle: 'Samouczek',
      calcTitle: 'Calculator',
      donateTitle: 'Donate',
      feedbackTitle: 'FeedBack',
      rectangleTitle: 'Rectangle',
      componentsTitle: 'Components'
    }
  },

  computed: {
    ...mapGetters(['getIconSize']),
    titleBanner () {
      let retTitle = ''
      switch (this.$route.fullPath) {
        case '/':
          retTitle = '' // this.homeTitle
          break
        case '/rectangle':
          retTitle = this.rectangleTitle
          break
        case '/calcpage':
          retTitle = this.calcTitle
          break
        case '/donatepage':
          retTitle = this.donateTitle
          break
        case '/feedbackpage':
          retTitle = this.feedBackTitle
          break
        case '/components':
          retTitle = this.componentsTitle
          break
      }
      return retTitle
    }
  }
}
</script>
