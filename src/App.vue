<template>

<div class="flex flex-col w-11/12 mx-auto sm:mx-10 my-5 sm:flex-row">
<my-button class="bg-sky-500" @click="userInfo.city_id=1">Заказать в Москву</my-button>
<my-button class="bg-teal-500 mt-3 sm:ml-4 sm:mt-0" @click="userInfo.city_id=2">Заказать в Санкт-Петербург</my-button>
<!-- <button @click="showWindow">Show</button> -->
</div>

<!-- <my-window v-model:show="windowVisible"/> -->

<success-window v-model:show="windowVisible"/>

 <div class="popup-modal fixed flex justify-center items-center inset-0 bg-gray-500 opacity-90 hidden">
    <div
      class="popup-content border rounded-lg p-6 mx-4 bg-white flex flex-col justify-center w-11/12 h-2/3 sm:h-1/3 lg:w-3/5">
      <p class="text-2xl font-medium">Заказать звонок</p>
      <form class="user-form sm:grid sm:grid-cols-3 sm:gap-x-6 lg:grid-cols-4" @submit.prevent="registerUser">
        <div class="mt-5">
          <label for="name" class="font-medium">Имя*</label>
          <input v-model="userInfo.name" type="text" name="name" id="name" placeholder="Иван Иванов" required
            class="border rounded-md w-full px-2 py-1 mt-1">
        </div>
        <div class="mt-5">
          <label for="tel-field" class="font-medium">Телефон*</label>
          <input v-model="userInfo.phone" id="tel-field" type="tel" name="phone" required placeholder="+7 (___) ___-__-__"
            class="border rounded-md w-full px-2 py-1 mt-1">
        </div>
        <div class="mt-5">
          <label for="email" class="font-medium">Email*</label>
          <input v-model="userInfo.email" type="email" name="email" id="email" placeholder="you@example.com" required
            class="border rounded-md w-full px-2 py-1 mt-1">
        </div>
        <div class="mt-5 sm:col-span-2 lg:col-span-1">
          <label for="city" class="font-medium">Город*</label>
          <select v-model="userInfo.city_id" id="city" class="border rounded-md w-full px-2 py-1 mt-1">
            <option v-for="city in cities"  :value="city.id">{{ city.name }}</option>
          </select>
        </div>
        <button type="submit"
          class="border rounded-md w-full mt-5 py-1 bg-green-500 text-white font-medium sm:h-8.5 sm:self-end lg:col-start-4 lg:col-end-5">Отправить</button>
      </form>
    </div>
  </div>



   <div @click="hideModal" class="popup-modal absolute flex justify-center items-center inset-0 bg-gray-500 opacity-90 hidden">
    <div
      class="popup-content relative border rounded-lg p-6 mx-4 bg-white flex flex-col justify-center w-11/12 h-1/3 lg:w-3/5">
      <p class="text-4xl font-bold uppercase text-center text-teal-500">Успешно</p>
    </div>
  </div>

</template>

<style>

</style>

<script>
  // Подключаем плагин ...
  import Inputmask from 'inputmask';
  import OrderButtons from './components/OrderButtons.vue';
  import MyButton from './components/MyButton';
  import MyPopup from './components/MyPopup';
  import MyWindow from './components/MyWindow.vue';
  import SuccessWindow from './components/SuccessWindow.vue';
  import axios from 'axios';
  export default {
  components: { OrderButtons, MyButton, MyPopup, MyWindow, SuccessWindow },
   mounted () {
    // ... используем
    var im = new Inputmask("+7 (999) 999-99-99");
    im.mask(document.getElementById('tel-field'));

   },
    data() {
      return {
        userInfo: {
          name:"",
          phone:"",
          email:"",
          city_id:""
        },
        cities: [
          {
          id: 1,
          name: "Москва"
          },
          {
          id: 2,
          name: "Санкт-Петербург"
          },
          {
          id: 3,
          name: "Казань"
          }
        ],
        windowVisible: false,

      }
    },
    methods: {
     hideModal(){
       let popupModal = document.querySelector('.popup-modal');
       popupModal.classList.toggle('hidden');
     },
     showWindow(){
       this.windowVisible=true;
     },
     async registerUser(){
       try {
      //  alert('УСПЕХ');
       let popupModal = document.querySelector('.popup-modal');
       popupModal.classList.add('hidden');
       this.windowVisible=true;
       this.userInfo.name="";
       this.userInfo.phone="";
       this.userInfo.email="";
       this.userInfo.city_id="";
      //  const finalInfo = await axios.post('');
       } catch (e) {
         alert('ОШИБКА')
       }
     }
     
   }
  };
  
</script>
