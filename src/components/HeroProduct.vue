<template>
  <section class="women-banner spad">
        <div class="container-fluid">
            <div class="row">
                <!-- if else vue -->
                <div class="col-lg-12 mt-5" v-if="products.length > 0">
                    <carousel class="product-slider" :items="3" :nav="false"  :autoplay="true" :dots="false">
                        <div class="product-item" v-for="itemProduct in products" v-bind:key="itemProduct.id">
                            <div class="pi-pic">
                                <img v-bind:src="itemProduct.galleries[0].photo" alt="" />
                                <ul>
                                        <!-- <router-link to="/cart"> -->
                                    <li class="w-icon active">
                                        <a @click="saveKeranjang(itemProduct.id,itemProduct.name,itemProduct.price,itemProduct.galleries[0].photo)" type="button"><i class="icon_bag_alt"></i></a>
                                    </li>
                                         <!-- </router-link> -->
                                    
                                    <li class="quick-view"><router-link v-bind:to="'/product/'+itemProduct.id">+ Quick View</router-link></li>
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">{{ itemProduct.type }}</div>
                                <router-link v-bind:to="'/product/'+itemProduct.id">
                                <h5>{{ itemProduct.name }}</h5>
                                <div class="product-price">
                                    RP. {{ itemProduct.price }}
                                    <!-- <span>$35.00</span> -->
                                </div>
                                </router-link>
                                
                                    
                            </div>
                        </div>
                        
                    </carousel>
                </div>
                
                <div class="col-lg-12" v-else>
                    <p>
                        Produk belum tersedia
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import carousel from 'vue-owl-carousel'
import axios from "axios"
export default {
    name:"HeroProduct",
  components: {
    carousel,
   
  },
  data(){
      return {
          products: [],
          keranjangUser:[]
      };
  },
  methods:{
       saveKeranjang(idProduct, nameProduct, priceProduct, photoProduct){
          var productStorage = {
              "id": idProduct,
              "name":nameProduct,
              "price": priceProduct,
              "photo":photoProduct
          }
          this.keranjangUser.push(productStorage);
          const parsed = JSON.stringify(this.keranjangUser);
          localStorage.setItem('keranjangUser', parsed);

          window.location.reload();
      },
  },
  mounted(){
    

    axios.get('http://127.0.0.1:8000/api/products')
      .then((response) =>
        // handle success
        this.products = response.data.data.data
      )
      .catch((error) =>
        // handle error
        console.log(error)
      )

        if (localStorage.getItem('keranjangUser')) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem('keranjangUser'));
      } catch(e) {
        localStorage.removeItem('keranjangUser');
      }
    }


  }

}
</script>

<style scoped>
.product-item{
    margin-right: 25px;
}

</style>