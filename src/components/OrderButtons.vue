<template>
<div class="flex flex-col w-11/12 mx-auto sm:mx-10 my-5 sm:flex-row">
<p>LOL</p>
<button @click="openModal" class="bg-sky-500 px-3 py-1 rounded-md text-white font-medium">Заказать в Москву</button>
<button @click="openModal" class="bg-teal-500 px-3 py-1 rounded-md text-white font-medium mt-3 sm:ml-4 sm:mt-0">Заказать в Санкт-Петербург</button>
</div>
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