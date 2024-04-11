<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'
import {ref} from 'vue'


const menuIsOpen = ref(false)

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
</script>

<template>
  <header>
    <nav>
      <ul>
        <li>
          
        </li>
      </ul>
    </nav>
    <button
    @pointerdown="menuIsOpen = !menuIsOpen"
    aria-controls="mainNav"
    aria-expanded="true"
    class="text-xL rounded-full border-2 #d97706 bg-red-300 px-2 text-3xl"
  >
    Menu
  </button>

  <Transition
  class="transition-transform duration-1000"
  enter-from-class="-translate-x-full"
  enter-to-class="translate-x-0"
  leave-active-class="-translate-x-full"
><!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
  <nav id="mainNav"
    v-show="menuIsOpen" >
    <ul>
      <li ><RouterLink to="/index" class="bg-purple-300 rounded-sm  "> Accueil </RouterLink></li>
      <li ><RouterLink to="/accordeon" class=" bg-purple-300  rounded-sm "> Accordeon </RouterLink></li>
      <li ><RouterLink to="/boucle" class="bg-purple-300 rounded-sm "> Boucle</RouterLink></li>
    </ul>
  </nav>
</Transition>
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
