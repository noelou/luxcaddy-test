<template>
  <div class="home overflow-hidden">
    <div class="lux-header-container flex fixed w-full px-10 z-10">
      <div class="flex flex-1 pt-6">
        <div class="logo-container">
          <img src="../assets/img/luxcaddyLogo.png">
        </div>
        <div class="px-10 w-full">
          <div class="flex items-center">
            <div class="search-input-container mr-2">
              <input type="text" placeholder="product search e.g. s" />
            </div>
            <img src="../assets/img/lupe.png" />
          </div>
          <div class="flex justify-end product-filter items-center pr-10 pt-1 relative">
            <span class="text-sm mr-1 relative z-20">product filter</span>
            <img class="sm-angle-down relative z-20" src="../assets/img/arrowD_s.png" />
            <div class="filter-container hidden absolute top-0 right-5 bg-white text-xs px-5 border-gray-400 border w-80 p-10 pb-2">
              <div class="flex-1">
                <div @click="filterItem(10,50)" class="pb-2 cursor-pointer">from 10 € to 50 €</div>
                <div @click="filterItem(50,100)" class="pb-2 cursor-pointer">from 50 € to 100 €</div>
                <div @click="filterItem(100,200)" class="pb-2 cursor-pointer">from 100 € to 200 €</div>
                <div @click="filterItem(200,1000)" class="pb-2 cursor-pointer">from 200 € to 1000 €</div>
              </div>
              <div @click="getProducts" class="cursor-pointer">Clear</div>
            </div>
          </div>
        </div>
      </div>
      <div class="flex items-center">
        <div class="p-6 cursor-pointer">
          <div class="h-7">
            <img src="../assets/img/key.png" class="m-auto" />
          </div>
          <span class="text-sm font-semibold">Login</span>
        </div>
        <div class="border-gray-500	border h-7 mt-1"></div>
        <div class="p-6 cursor-pointer">
          <div class="h-7">
            <img src="../assets/img/karre.png" class="m-auto" />
          </div>
          <span class="text-sm font-semibold">Delivery</span>
        </div>
        <div class="border-gray-500	border h-7 mt-1"></div>
        <div class="p-6 cursor-pointer">
          <div class="h-7">
            <img src="../assets/img/info.png" class="m-auto" />
          </div>
          <span class="text-sm font-semibold">Blog</span>
        </div>
        <div class="border-gray-500 border h-7 mt-1"></div>
        <div class="flex help-nav-container px-6 cursor-pointer">
          <div class="">
            <div class="h-7">
              <img src="../assets/img/help.png" class="m-auto" />
            </div>
            <span class="text-sm font-semibold">Help</span>
          </div>
          <img src="../assets/img/arrowD_s.png" class="pl-2 sm-angle-down mt-2" />
        </div>
        <div class="border-gray-500 border h-7 mt-1"></div>
        <div class="p-6 cursor-pointer">
          <div class="h-7">
            <img src="../assets/img/flag_en.png" class="m-auto" />
          </div>
          <span class="text-sm font-semibold">Language</span>
        </div>
      </div>
    </div>
    <div class="flex lux-body-container px-10">
      <div class="side-nav-selector flex flex-col h-full w-1/5">
        <ul class="text-left">
          <li>NEW PRODUCTS</li>
          <li>SPECIAL OFFERS</li>
          <li>Candlemas</li>
          <li>Specialties from the World</li>
          <li>Healthy food</li>
          <li>Organic Products</li>
          <li>Catering</li>
          <li>Butcher</li>
          <li>Fruit and vegetables</li>
          <li>Dairy products</li>
          <li>Seafood</li>
          <li>Bakery</li>
          <li>Deep Frozen</li>
          <li>Savoury Groceries</li>
          <li>Sweet Groceries</li>
          <li>Drinkshop</li>
          <li>Wine shop</li>
          <li>Body care</li>
          <li>Household</li>
          <li>Baby & Children</li>
          <li>Pets</li>
          <li>Partner Shops</li>
        </ul>
      </div>
      <div class="w-3/5 list-body-container relative">
        <div class="list-header-img">
          <img src="../assets/img/asian-corner.jpg" class="w-full" />
        </div>
        <div class="flex flex-wrap product-container">
          <div v-for="list in listData" :key="list.id" class="p-2 relative product-details">
            <router-link :to="{name: 'Product',params: {id:list.id}} " :list="list">
              <div class="cursor-pointer hover px-2">
                <div class="shopping-unit-price mt-8">
                  <div class="text-xs text-gray-600">Unit price:</div>
                  <div class="text-sm">{{ list.price }} €/ut</div>
                </div>
                <div class="shopping-my-shop text-sm mb-1">
                  <input type="checkbox" /> MyShop
                </div>
                <div class="shopping-list-btn-container">
                  <button class="text-white font-bold w-full text-xs py-1 px-2 flex items-center">
                    <img src="../assets/img/butt_alist.png" class="mr-2">
                    SHOPPING LISTS
                  </button>
                </div>
              </div>
              <div class="text-left font-bold text-sm leading-none h-14">{{ list.title }}</div>
              <div class="flex items-center img-container">
                <img class="m-auto" :src="list.image">
              </div>
            </router-link>
            <div class="">
              <div class="text-right font-bold text-2xl">{{ list.price }} €</div>
              <div>
                <button class="text-left add-cart-btn text-white font-bold w-full text-xs py-1 px-2 flex">
                  <img src="../assets/img/butt_Add.png" class="but-add-img mr-2">
                  ADD TO CART
                </button>
              </div>
            </div>
          </div>
        </div>
        <Footer class="m-2" />
        <Loading  v-if="showLoading" />
      </div>
      <div class="w-1/5">
        <div class="cart">
          <div class="flex cart-header text-left font-bold px-2 py-1 relative">
            <div class="flex-1">Cart ( 1 )</div>
            <div>16.22 €</div>
            <div class="boxArrowD absolute">
              <img src="../assets/img/boxArrowD.png">
            </div>
          </div>
          <div class="px-2 pb-2 pt-4">
            <div class="flex justify-end items-center pb-4">
              <div class="w-3/12">
                <img src="../assets/img/lupePlus.png" class="m-auto cursor-pointer">
              </div>
              <div class="seperator h-4 border-gray-500 border"></div>
              <div class="w-3/12">
                <img src="../assets/img/bin.png" class="m-auto cursor-pointer">
              </div>
              <div class="seperator h-4 border-gray-500 border"></div>
              <div class="w-3/12">
                <img src="../assets/img/disk.png" class="m-auto cursor-pointer">
              </div>
              <div class="seperator h-4 border-gray-500 border"></div>
              <div class="flex items-center w-3/12 justify-center">
                <img src="../assets/img/list.png" class="m-auto cursor-pointer">
                <img src="../assets/img/arrowD_s.png" class="sm-angle-down h-1.5 w-2" />
              </div>
            </div>
            <div class="cart-box bg-white pt-2">
              <div class="text-center font-semibold text-base leading-none mt-10">Your cart is<br>currently empty.</div>
            </div>
            <div class="checkout flex items-center text-left bg-white py-4 px-2">
              <div class="flex-1">Checkout</div>
              <div>
                <img src="../assets/img/checkout.png">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Footer from "../components/Footer.vue";
import Loading from "../components/Loading.vue";
import { ref, onMounted } from "vue";
import axios from "axios";
import _ from 'lodash';

export default {
  name: 'Home',
  components: {
    Footer,
    Loading
  },
  setup() {
    const productsData = ref([]);
    const listData = ref([]);
    const showLoading = ref(false);

    onMounted(() => {
      getProducts();
    });

    async function getProducts() {
      showLoading.value = true;
      await axios.get(
        "https://fakestoreapi.com/products"
      )
      .then((res) => {
        productsData.value = res.data;
        listData.value = _.sortBy(productsData.value,['title','price'])
        showLoading.value = false;
      })
    }

    async function filterItem( a,b ) { 
      listData.value = _.filter(productsData.value, function(o) {
        return o.price > a && o.price < b ;
      })
    }

    return {
      productsData,
      getProducts,
      listData,
      showLoading,
      filterItem,
    }
  }
}
</script>
