<template>
  <div class="home">
     <Header />
     <HeroSection />
      
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/Header.vue'

import HeroSection from '@/components/HeroSection.vue'

export default {
  name: 'Home',
  components: {
    // HelloWorld
    Header,
    // carousel,
    HeroSection
  }
}
</script>
