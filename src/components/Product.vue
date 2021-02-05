<template>
  <div class="home overflow-hidden">
    <div class="lux-header-container flex fixed w-full px-10">
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
          <div class="flex justify-end product-filter items-center pr-10 pt-1">
            <span @click="sortItem()" class="text-sm">product filter</span>
            <img class="sm-angle-down" src="../assets/img/arrowD_s.png" />
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
      <div class="w-3/5 list-body-container">
       <div>{{ $route.params.id }}</div>
       <div>{{ $route.params }}</div>
      </div>
      <div class="w-1/5">
        <div class="cart">
          <div class="flex cart-header text-left font-bold px-2 py-1">
            <div class="flex-1">Cart (1)</div>
            <div>16.22</div>
          </div>
          <div class="p-2">
            <div class="flex justify-end">
              <div>
                <img src="../assets/img/lupePlus.png">
              </div>
              <div class="seperator"></div>
              <div>
                <img src="../assets/img/bin.png">
              </div>
              <div class="seperator"></div>
              <div>
                <img src="../assets/img/disk.png">
              </div>
              <div class="seperator"></div>
              <div>
                <img src="../assets/img/list.png">
              </div>
            </div>
            <div class="cart-box bg-white pt-2"></div>
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
import { onMounted } from "vue";

export default {
  name: 'Home',
  components: {
  },
  props: ['list'],
  setup(props) {
    
    onMounted(() => {
      console.log(props.list)
    });
  }
}
</script>
