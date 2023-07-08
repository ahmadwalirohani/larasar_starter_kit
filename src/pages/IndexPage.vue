<template>
  <q-page ref="Page" >
    <div class="q-pa-md">
      <div class="q-gutter-y-md" style="max-width: 100%;">
        <q-tabs v-model="sub_models" align="justify" dense class="text-grey-10">
          <q-tab icon="mail" label="Mail" name="mail" />
          <q-tab icon="mail" label="Mail" name="mails" />
          <q-tab icon="mail" label="Mail" name="mail2" />
          <q-tab icon="mail" label="Mail" name="mail4" />
        </q-tabs>
      </div>
    </div>
    <div class="main-view" >
      {{ Page }}
      <q-table class="main-table shadow-24">

      </q-table>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  setup() {
    const Page = ref();
    console.log(Page.value);
    return {
      Page,
      sub_models: ref('mail')
    }
  }
});

</script>

<style lang="sass">
.main-view
  width: 100%
  padding: 10px
  height: 100%

.main-table
  height: 100%

  thead tr:first-child th
    /* bg color is important for th; just specify one */
    background-color: lightgrey
  thead tr th
    position: sticky
    z-index: 1
  thead tr:first-child th
    top: 0

  /* this is when the loading indicator appears */
  &.q-table--loading thead tr:last-child th
    /* height of all previous header rows */
    top: 3px
</style>
