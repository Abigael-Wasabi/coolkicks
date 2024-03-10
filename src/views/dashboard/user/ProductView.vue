<template>
  <v-layout>
    <v-app-bar title="User Dashboard"></v-app-bar>

    <v-navigation-drawer permanent>
      <v-list>
        <v-list-item to="#" title="Dashboard" prepend-icon="mdi-home" style="text-align: left;"></v-list-item>
        <v-list-item :to="{ name: 'user-profile' }" title="UserProfile" prepend-icon="mdi-account" style="text-align: left;"></v-list-item>
        <v-list-item :to="{ name: 'user-product' }" title="Products" prepend-icon="mdi-book" style="text-align: left;"></v-list-item>
        <v-list-item @click="logout" title="Logout" prepend-icon="mdi-logout" style="text-align: left;"></v-list-item>
      </v-list>
      <h4 class="mt-80 font-bold text-left">CORNER STORE</h4>
    </v-navigation-drawer>

    <v-main>
      <table class="min-w-full border border-gray-300 mt-6">
        <thead>
          <tr>
            <th class="border border-gray-300 px-4 py-2">Product Name</th>
            <th class="border border-gray-300 px-4 py-2">Price</th>
            <th class="border border-gray-300 px-4 py-2">Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(product, index) in products" :key="index">
            <td class="border border-gray-300 px-4 py-2">{{ product.name }}</td>
            <td class="border border-gray-300 px-4 py-2">{{ product.price }}</td>
            <td class="border border-gray-300 px-4 py-2">
              <button @click="editProduct(product)" class="text-blue-500 hover:text-blue-700 mr-2">Edit</button>
              <button @click="deleteProduct(index)" class="text-red-500 hover:text-red-700">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>

      <button @click="openAddModal" class="mt-4 bg-green-500 hover:bg-green-700 text-slate-900 font-semibold py-2 px-4 rounded">
        Add Product
      </button>

      <product-modal :is-modal-open="isModalOpen" :modal-mode="modalMode" @close="closeModal" @save="saveProduct" />
    </v-main>
  </v-layout>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';
import ProductModal from './ProductModal.vue'; // Import the modal component

const router = useRouter();

const logout = async () => {
  const token = localStorage.getItem('token');
  try {
    await axios.post(
      'http://localhost:8000/api/user/logout',
      {},
      {
        headers: {
          Authorization: `Bearer ${token}`,
        },
      }
    );
    localStorage.removeItem('token');
    router.push('/');
  } catch (error) {
    console.log(error);
  }
};

const isModalOpen = ref(false);
const modalMode = ref('add');

const openAddModal = () => {
  isModalOpen.value = true;
};

const closeModal = () => {
  isModalOpen.value = false;
};

const saveProduct = () => {
  // Handle saving the product (add or edit) here
  closeModal();
};

const editProduct = (product) => {
  modalMode.value = 'edit';
  openAddModal();
};

const deleteProduct = (index) => {
  // Handle product deletion here
};

const products = ref([
  // Your products data array
]);

</script>

<style scoped>
/* Your component's CSS styling */
</style>
