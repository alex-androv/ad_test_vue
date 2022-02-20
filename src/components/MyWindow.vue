<template>
   <div v-if="show" @click.stop="hideWindow" class="popup-modal absolute flex justify-center items-center inset-0 bg-gray-500 opacity-90 hidden">
    <div @click.stop
      class="popup-content border rounded-lg p-6 mx-4 bg-white flex flex-col justify-center w-11/12 h-2/3 sm:h-1/3 lg:w-3/5">
      <p class="text-2xl font-medium">Заказать звонок!!!!!</p>
      <form class="sm:grid sm:grid-cols-3 sm:gap-x-6 lg:grid-cols-4">
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
            <option v-for="city in cities" :value="city.id">{{ city.name }}</option>
          </select>
        </div>
        <button type="submit"
          class="border rounded-md w-full mt-5 py-1 bg-green-500 text-white font-medium sm:h-8.5 sm:self-end lg:col-start-4 lg:col-end-5">Отправить</button>
      </form>
    </div>
  </div>
</template>

<script>
import Inputmask from 'inputmask';
    export default {
       name:"my-window",
    //    props: {
    //        show: {
    //            type: Boolean,
    //            default:false
    //        }
    //    },
       mounted () {
    // ... используем
    var im = new Inputmask("+7 (999) 999-99-99");
    im.mask(document.getElementById('tel-field'));

   },
       methods: {
           hideWindow () {
               this.$emit("update:show", false)
           }
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
    }
</script>

<style scoped>

</style>