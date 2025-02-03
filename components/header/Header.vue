<template>
  <div
    class="fixed flex items-center w-full h-14 lg:h-20 z-10 backdrop-blur-md bg-[rgba(255,255,255,0.5)]"
  >
    <div class="container mx-auto flex justify-between items-center">
      <Logo class="logo" />
      <div class="flex">
        <Nav :links="links" class="header-nav hidden lg:block" />
      </div>
    </div>
    <BtnBurger
      @click="toggleBurger"
      :isMenu="isMenu"
      class="absolute right-0 mr-4 z-50 lg:hidden p-1"
    />
    <Menu @nav-click="toggleLink" :isMenu="isMenu" />
  </div>
</template>

<script setup lang="ts">
import { links } from './type'

let isMenu = ref<boolean>(false)

function toggleBurger(event: MouseEvent) {
  isMenu.value = !isMenu.value
  toggleClassNoScrooll()
}

function toggleLink(event: MouseEvent) {
  isMenu.value = !isMenu.value
  toggleClassNoScrooll()
}

function toggleClassNoScrooll() {
  const element = document.querySelector('html')
  isMenu.value
  if (isMenu.value) {
    element?.classList.add('no-scroll')
  } else {
    element?.classList.remove('no-scroll')
  }
}

//
</script>

<style scoped lang="scss">
.header-nav :deep(.nav__block) {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}
.header-nav :deep(.nav__link) {
  color: black;
}
</style>
