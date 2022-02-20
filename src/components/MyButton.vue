<template>

<button @click="openModal" class="border px-3 py-1 rounded-md text-white font-medium"><slot></slot></button>

</template>

<script>
    export default {
    methods: {
     openModal(){
       let popupModal = document.querySelector('.popup-modal');
       popupModal.classList.remove('hidden');
     }
   }
    }
</script>

<style scoped>

</style>