<template>
    <div>
        <header class="bg-blue py-4 sticky top-0 z-10">
      <div class="flex items-center justify-between px-4">
        <div class="flex items-center space-x-4">
          <div class="flex items-center bg-white rounded-full p-2">
            <img src="@/assets/image/logo.png" alt="Restaurant Logo" class="w-8 h-8">
          </div>
          <h1 class="text-white text-4xl font-bold">Manjo Makang!!!</h1>
        </div>
        <div class="text-white flex items-center space-x-2">
          <div class="border border-white rounded-lg p-2">
            <p class="text-lg font-semibold">{{ currentTime }}</p>
          </div>
          <div>
            <p class="text-sm text-white opacity-80">{{ currentDate }}</p>
          </div>
        </div>
      </div>
    </header>
  
      <main class="container mx-auto my-8">
        <h2 class="text-3xl font-bold mb-6">Menu</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-8">
          <div v-for="item in menuItems" :key="item.id">
            <div class="card bg-white rounded-lg shadow-lg">
              <div class="card-body p-4">
                <div class="relative w-full h-40 rounded-lg overflow-hidden">
                  <img :src="getImagePath(item.image)" :alt="item.name" class="w-full h-full object-cover border border-gray-200">
                </div>
                <h3 class="text-lg font-semibold mt-4">{{ item.name }}</h3>
                <p class="text-gray-600">{{ item.description }}</p>
                <p class="text-gray-600 font-bold mt-2">{{ item.harga }}</p>
                <div class="flex justify-between mt-4">
                  <button @click="addToCart(item)" class="btn btn-primary">Review</button>
                  <button @click="viewDetails(item)" class="btn btn-secondary">Check</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
  
      <footer class="bg-gray-800 py-4">
        <p class="text-white text-center">© 2023 Restaurant Name. All rights reserved.</p>
      </footer>
    </div>
  </template>

  
  <script>
  export default {
    name: 'RestaurantMenu',
    data() {
      return {
        menuItems: [
        { id: 1, name: 'Paket Soto 1', description: 'Coto Babi + Nasi', harga: 'Rp 25.000', image: 'soto.png', category: 'food' },
        { id: 2, name: 'Paket Soto 2', description: 'Nasi Ragey + Kuah Coto',  harga: 'Rp 20.000', image: 'soto2.png', category: 'food' },
        { id: 3, name: 'Mie Ceplok', description: 'Mie Ceplok no bro',  harga: 'Rp 10.000', image: 'ragey.png', category: 'food' },
        { id: 4, name: 'Ragey', description: '1/Ragey',  harga: 'Rp 5.000', image: 'ragey_satu.png', category: 'food' },
        { id: 5, name: 'Nasi Putih', description: '1 Porsi nda ada stenga2',  harga: 'Rp 5.000', image: 'nasi_putih2.png', category: 'food' },
        { id: 6, name: 'Nasi Putih', description: '1 Porsi nda ada stenga2',  harga: 'Rp 4.000', image: 'telur_rebus.png', category: 'food' },
        { id: 7, name: 'Coffee 1', description: 'Coffee Description 1',  harga: 'Rp 5.000', image: 'coffee.png', category: 'coffee' },
        { id: 8, name: 'Beverage 1', description: 'Beverage Description 1',  harga: 'Rp 5.000', image: 'teh_hangat.png', category: 'beverage' },
        { id: 9, name: 'Beverage 2', description: 'Beverage Description 2',  harga: 'Rp 5.000', image: 'nutrisari.png', category: 'beverage' },
        ],
      };
    },
    computed: {
    currentDate() {
      const now = new Date();
      return now.toLocaleDateString();
    },
    currentTime() {
      const now = new Date();
      return now.toLocaleTimeString();
    },
  },
    methods: {
      getImagePath(imageName) {
        return require(`@/assets/image/${imageName}`);
      },
      addToCart(item) {
        // Handle the click event for the "Add to Cart" button
        console.log('Add to Cart:', item);
        // You can customize this method to add the item to the cart or perform any desired actions
      },
      viewDetails(item) {
        // Handle the click event for the "View Details" button
        console.log('View Details:', item);
        // You can customize this method to show additional details or perform any desired actions
      },
    },
  };
  </script>
  
  <style scoped>
.container {
  max-width: 1200px;
}

.grid {
  gap: 2rem;
}

.bg-blue {
  background-color: #2b6cb0;
}

.bg-gold {
  background-color: #d69e2e;
}

.text-white {
  color: #fff;
}

.text-center {
  text-align: center;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.relative {
  position: relative;
}

.object-cover {
  object-fit: cover;
}

.text-lg {
  font-size: 1.125rem;
}

.mt-2 {
  margin-top: 0.5rem;
}

.text-gray-600 {
  color: #4b5563;
}

.font-bold {
  font-weight: 700;
}

.mt-4 {
  margin-top: 1rem;
}

.btn {
  padding: 0.5rem 1rem;
}

.btn-primary {
  background-color: #2b6cb0;
  color: #fff;
  transition: background-color 0.3s ease;
}

.btn-primary:hover {
  background-color: #2563af;
}

.btn-secondary {
  background-color: #fff;
  color: #2b6cb0;
  border: 1px solid #2b6cb0;
  transition: background-color 0.3s ease;
}

.btn-secondary:hover {
  background-color: #f0f4ff;
}


/* Custom styles for header */
header {
  transition: background-color 0.3s;
}

header:hover {
  background-color: #2a4365;
}

header img {
  cursor: pointer;
}

header h1 {
  cursor: pointer;
}

header p {
  cursor: default;
}

/* Custom styles for the logo container */
header .logo-container {
  background-color: #fff;
}
</style>
