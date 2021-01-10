<template>
  <div class="home">
     <Header />
     <HeroSection />
     <HeroProduct />
     <Instagram />
     <PartnerLogo />
     <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Header from '@/components/Header.vue'

import HeroSection from '@/components/HeroSection.vue'
import HeroProduct from '@/components/HeroProduct.vue'
import Instagram from '@/components/Instagram.vue'
import PartnerLogo from '@/components/PartnerLogo.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'Home',
  components: {
    Header,
    HeroSection,
    HeroProduct,
    Instagram,
    PartnerLogo,
    Footer
  }
}
</script>
