<template>
  <div class="home">
    <Personagens />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Personagens from '@/components/Characters.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    Personagens
  }

  
}
</script>
