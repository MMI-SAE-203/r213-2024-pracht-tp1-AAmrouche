<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'
import {ref} from 'vue'


const sectionOpen = ref(0)


onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
</script>

<template>

    <section>
        <button class="text-xl" @pointerdown= "sectionOpen = 1" >bouton 1</button>
        <p v-show="sectionOpen==1 ">Lorem ipsum dolor sit amet consectetur adipisicing elit. Totam doloribus atque omnis, delectus quos dignissimos. Praesentium nihil quas qui natus odio illo impedit dolor, reprehenderit delectus eos? Dolore, consequuntur saepe?</p>
    </section>
    <section>
        <button class="text-xl" @pointerdown= "sectionOpen = 2">bouton 2</button>
        <p v-show="sectionOpen==2">Eveniet minima eius aut quod, libero accusantium, blanditiis quidem, aliquam reprehenderit saepe reiciendis aperiam ipsam obcaecati facilis excepturi sint laudantium voluptates voluptatibus assumenda ullam numquam tenetur qui omnis nemo! Aspernatur.</p>
    </section>
    <section>
        <button class="text-xl" @pointerdown= "sectionOpen = 3">bouton 3</button>
        <p v-show="sectionOpen==3" >Velit praesentium odio, facere non sequi autem voluptates unde laboriosam ullam quos, accusamus quibusdam cum ad architecto minus quia! Asperiores ab iste repellat facere soluta rerum provident ipsam totam hic?</p>
    </section>

</template>