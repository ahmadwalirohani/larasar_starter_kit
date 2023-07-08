<template>
  <q-layout view="hHh LpR lff">
    <q-header elevated class="bg-main-gradient">
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          App Title
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg" :width="200" elevated :breakpoint="400">
      <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
        <q-list>

          <template v-for="(model, i) in DrawerModelList" :key="i">
            <q-item clickable  :active="model.is_active"
              @click="OnDrawerModelFn(i)"
              active-class="bg-main-gradient text-white" v-ripple>
              <q-item-section avatar>
                <q-icon :color="model.is_active ? 'white' : 'black'" :name="model.icon" />
              </q-item-section>
              <q-item-section>
                <q-item-label>{{ model.title }}</q-item-label>
              </q-item-section>
            </q-item>
          </template>

        </q-list>
      </q-scroll-area>
      <q-img class="absolute-top" src="/material.png" style="height: 150px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">

          </q-avatar>
          <div class="text-weight-bold"></div>
          <div></div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container style="    background: linear-gradient(90deg,#ece9e6,#fff);">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'


const ModelList = [
  {
    title: 'Dashboard',
    icon: 'home',
    link: 'https://quasar.dev',
    is_active: true,
    is_enabled: true
  },
  {
    title: 'Accounts',
    icon: 'account_balance',
    link: 'https://quasar.dev',
    is_active: false,
    is_enabled: false
  },
  {
    title: 'Inventory',
    icon: 'domain',
    link: 'https://quasar.dev',
    is_active: false,
    is_enabled: false
  },
  {
    title: 'POS',
    icon: 'add_shopping_cart',
    link: 'https://quasar.dev',
    is_active: false,
    is_enabled: false
  },
  {
    title: 'Finance',
    icon: 'money',
    link: 'https://quasar.dev',
    is_active: false,
    is_enabled: true
  },
  {
    title: 'Setting',
    icon: 'settings',
    link: 'https://quasar.dev',
    is_active: false,
    is_enabled: true
  },
];

export default defineComponent({
  name: 'MainLayout',

  components: {
  },

  setup() {
    const leftDrawerOpen = ref(false)
    const DrawerModelList = ref(ModelList);
    return {
      DrawerModelList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      OnDrawerModelFn(model) {
        DrawerModelList.value.forEach((e,i)=>{
          e.is_active = ( i == model && e.is_enabled) ? true : false ;
        })
      }
    }
  }
})
</script>
<style lang="sass">
.bg-main-gradient
  background: linear-gradient(90deg,#606c88,#3f4c6b) !important
</style>
