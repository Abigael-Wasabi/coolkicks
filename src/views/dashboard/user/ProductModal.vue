<template>
    <div v-if="isModalOpen" class="fixed inset-0 flex items-center justify-center bg-gray-800 bg-opacity-75">
      <div class="bg-white rounded-lg p-6">
        <h2 class="text-lg font-semibold mb-4">{{ modalMode === 'add' ? 'Add Product' : 'Edit Product' }}</h2>
        <!-- Form fields for adding/editing products -->
        <input v-model="productName" placeholder="Product Name" class="border p-2 mb-2" />
        <input v-model="productPrice" placeholder="Product Price" class="border p-2 mb-4" />
        <button @click="saveProduct" class="bg-blue-500 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded">
          {{ modalMode === 'add' ? 'Add' : 'Save' }}
        </button>
        <button @click="closeModal" class="bg-gray-500 hover:bg-gray-700 text-white font-semibold py-2 px-4 rounded ml-2">
          Cancel
        </button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    props: {
      isModalOpen: Boolean,
      modalMode: String,
    },
    emits: ['close', 'save'],
    setup(props) {
      const productName = ref('');
      const productPrice = ref('');
  
      const closeModal = () => {
        productName.value = '';
        productPrice.value = '';
        props.close();
      };
  
      const saveProduct = () => {
        // Handle saving the product (add or edit) here
        // Use productName.value and productPrice.value to access the input values
        props.save();
        closeModal();
      };
  
      return {
        productName,
        productPrice,
        closeModal,
        saveProduct,
      };
    },
  };
  </script>
  
  <style scoped>
  /* Your modal component's CSS styling */
  </style>
  