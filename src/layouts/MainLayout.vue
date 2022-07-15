<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
      </q-toolbar>

        <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Список завдань</div>
        <div class="text-subtitle1">{{ todaysDate }} (мені поки що лінь займатися перекладом дати)</div>
      </div>
      <q-img 
        src="../statics/flag.jpg"
        class="header-image absolute-top"
      />
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
        <q-list padding>
          <q-item 
            clickable 
            v-ripple
            to="/"
            exact  
          >
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>
            <q-item-section>
              Список завдань
            </q-item-section>
          </q-item>
          <q-item 
            clickable 
            v-ripple
            to="/help"
          >
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section>
              Допомога
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

        <q-img class="absolute-top" src="../statics/flag.jpg" style="height: 192px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://s.gravatar.com/avatar/bf1c488ad98c40fc3c689551bfa85a12?s=80">
            </q-avatar>
            <div class="text-weight-bold">Oleg Yerokhin</div>
            <div>@OlegYerokhin</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'
import { computed } from 'vue';

export default {
  name: 'MainLayout',
  data () {
    return {
      leftDrawerOpen: false,
    }
  },

  computed: {
    todaysDate() {
      const timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd D MMMM YYYY')
    }
  }
}
</script>

<style lang="scss" scoped>
  .header-image {
    height: 100%;
    z-index: -1;
    filter: grayscale(50%);
  }
</style>