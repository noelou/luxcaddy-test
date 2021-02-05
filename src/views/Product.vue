<template>
  <div class="home overflow-hidden">
    <div class="lux-header-container flex fixed w-full px-10 z-20">
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
      <div class="w-3/5 list-body-container px-4 relative">
       <div class="flex">
         <div class="flex-1 ">
           <div class="text-3xl font-bold mb-4 w-11/12">{{ productData.title }}</div>
         </div>
         <div>
           <router-link to="/">
            <button class="close-btn rounded py-2 px-6">❌</button>
           </router-link>
         </div>
       </div>
        <div class="flex w-full mt-10">
          <div class="w-2/5">
            <div>
              <div class="border-gray-200	border-b text-xs pb-1 mb-1">UNIT PRICE</div>
              <div>{{ productData.price }} €/ut</div>
            </div>
            <div class="">
              <div class="text-right text-lightGreen font-bold text-3xl">{{ productData.price }} €</div>
              <div class="flex">
                <div class="flex adder-container mr-2">
                  <div class="">
                    <input type="number" class="text-right pr-1 text-xl font-bold" value="0" />
                  </div>
                  <div>
                    <div class="add-minus cursor-pointer font-bold plus flex items-center">
                      <span>+</span>
                    </div>
                    <div class="add-minus cursor-pointer minus flex items-baseline">
                      <span>-</span>
                    </div>
                  </div>
                </div>
                <div class="w-full">
                  <button class="add-cart-btn text-white h-full font-bold text-sm w-full">ADD TO CART</button>
                </div>
              </div>
              <div class="border-gray-200	border-t mt-3">
                <button class="py-0 px-2 flex items-center shopping-list-btn rounded-b"><span class="mr-2">≡</span> <span class="text-xs">Shopping Lists</span></button>
              </div>
            </div>
          </div>
          <div class="w-3/5 selected-product-img ml-10">
            <img :src="productData.image" class="w-56 m-auto" />
          </div>
        </div>
        <div class="mt-20">
          <div class="mb-10">
            <div class="border-gray-200	border-b text-xs pb-1 mb-2">DESCRIPTION:</div>
            <div class="text-sm leading-normal">{{ productData.description }}</div>
          </div>
          <div class="mb-10">
            <div class="border-gray-200	border-b text-xs pb-1 mb-2">CATEGORIES:</div>
            <div class="capitalize text-lightGreen font-semibold">
              <span class="text-black mr-2">❯</span> {{ productData.category }}
            </div>
          </div>
          <div>
            <div class="border-gray-200	border-b text-xs pb-1 mb-2">ALLERGENS*</div>
            <div>No allergens</div>
          </div>
          <p class="mt-10 text-xs">*ALWAYS check the informations on the products before consommation. Data and images on this page are not contractual.</p>
        </div>
        <Footer />
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
import { useRoute } from "vue-router";
import axios from "axios";

export default {
  name: 'Home',
  components: {
    Footer,
    Loading
  },
  setup() {
    const route = useRoute();
    const productData = ref({});
    const showLoading = ref(false);

    onMounted(() => {
      getSpecificProductData();
    });

    async function getSpecificProductData() {
      let id = route.params.id;
      showLoading.value = true;

      await axios.get(
        "https://fakestoreapi.com/products/" + id
      )
      .then((res) => {
        productData.value = res.data;
        showLoading.value = false;
      })
      
    }

    return {
      getSpecificProductData,
      productData,
      showLoading
    }
  }
}
</script>
