<template>
  <div class="main-container-layout">
    <section class="header-wrapper border-b border-gray-200 border-b-solid">
      <HeaderComp/>
    </section>
    <div class="body-wrapper">
      <section class="border-r border-gray-200 border-r-solid" :class="[ isCollpased ? 'side-wrapper__collapse' : 'side-wrapper' ]">
        <SideBarComp @collapsed="onCollapsedChange" @menuItemChange="onMenuItemChange"/>
      </section>
      <section class="content-wrapper">
        <component :is="currentPage"/>
      </section>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import HeaderComp from './Header.vue'
import SideBarComp from './Side.vue'

import Page1 from './Page1.vue'
import Page2 from './Page2.vue'
import Page3 from './Page3.vue'

const isCollpased = ref(false)

const pageList = [
  {
    name: 'page1',
    component: Page1
  },
  {
    name: 'page2',
    component: Page2
  },
  {
    name: 'page3',
    component: Page3
  },
]

const currentPage = ref(pageList.find(it => it.name === 'page1')?.component)

function onCollapsedChange(params:boolean) {
  isCollpased.value = params
}
function onMenuItemChange(params: string) {
  currentPage.value = pageList.find(it => it.name === params)?.component
}
</script>
