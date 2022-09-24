<template>
  <nav class="bg-gray-900 shadow-lg">
    <div class="w-full mx-auto px-4">
      <div class="flex justify-between">
        <div>
          <!-- Website Logo -->
          <a href="#/" class="flex items-center py-4 px-2">
            <span class="font-oswald font-black text-gray-50 uppercase text-lg">FastAndSlim</span>
          </a>
        </div>
        <!-- Primary Navbar items -->
        <div class="hidden md:flex items-center space-x-1 font-oswald uppercase">
          <a href="#/"
            class="py-4 px-2 text-gray-50 font-semibold hover:text-orange-700 transition duration-300">Home</a>
          <a href="#/about_us" class="py-4 px-2 text-gray-50 font-semibold hover:text-orange-700 transition duration-300">Despre
            noi</a>
          <a href="#/packages"
            class="py-4 px-2 text-gray-50 font-semibold hover:text-orange-700 transition duration-300">Programe</a>
          <a href=""
            class="py-4 px-2 text-gray-50 font-semibold hover:text-orange-700 transition duration-300">Transformari</a>
          <a href="" class="py-4 px-2 text-gray-50 font-semibold hover:text-orange-700 transition duration-300">Nutritie
            &amp; Fitness</a>
          <a href=""
            class="py-4 px-2 text-gray-50 font-semibold hover:text-orange-700 transition duration-300">Contact</a>
        </div>
        <!-- Mobile menu button -->
        <div class="md:hidden flex items-center">
          <button class="outline-none mobile-menu-button" @click="toggleMenu">
            <svg class=" w-6 h-6 text-gray-50 hover:text-orange-700" x-show="!showMenu" fill="none"
              stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor">
              <path d="M4 6h16M4 12h16M4 18h16"></path>
            </svg>
          </button>
        </div>
      </div>
      <!-- mobile menu -->
      <div class="mobile-menu" :class="{ hidden: !showMenu }">
        <ul class="text-gray-50">
          <li>
            <a href="#/" class="block w-full text-sm px-2 py-4 hover:bg-orange-700 transition duration-300">Home</a>
          </li>
          <li>
            <a href="#/about_us" class="block w-full text-sm px-2 py-4 hover:bg-orange-700 transition duration-300">Despre noi</a>
          </li>
          <li>
            <a href="#/packages" class="block w-full text-sm px-2 py-4 hover:bg-orange-700 transition duration-300">Programe</a>
          </li>
          <li>
            <a href=""
              class="block w-full text-sm px-2 py-4 hover:bg-orange-700 transition duration-300">Transformari</a>
          </li>
          <li>
            <a href="" class="block w-full text-sm px-2 py-4 hover:bg-orange-700 transition duration-300">Nutritie &amp;
              Fitness</a>
          </li>
          <li>
            <a href="" class="block w-full text-sm px-2 py-4 hover:bg-orange-700 transition duration-300">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <component :is="currentView" />
</template>

<script>
import AboutUsPage from './AboutUsPage.vue';
import HomePage from './HomePage.vue';
import PackagesPage from './PackagesPage.vue';


const routes = {
  '/': HomePage,
  '/packages': PackagesPage,
  '/about_us': AboutUsPage
}

export default {
  name: 'AppMenu',
  props: {},
  data() {
    return {
      showMenu: false,
      currentPath: window.location.hash,
    };
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/'] //|| NotFound
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
