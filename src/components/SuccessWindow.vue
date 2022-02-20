<template>
   <div v-if="show" @click.stop="hideWindow" class="absolute flex justify-center items-center inset-0 bg-gray-500 opacity-90">
    <div @click.stop
      class="popup-content border rounded-lg p-6 mx-4 bg-white flex flex-col justify-center w-11/12 h-2/3 sm:h-1/3 lg:w-3/5">
      <p class="text-4xl font-bold uppercase text-center text-teal-500">Успешно</p>
    </div>
  </div>
</template>

<script>
    export default {
       name:"success-window",
       props: {
           show: {
               type: Boolean,
               default:false
           }
       },
       methods: {
           hideWindow () {
               this.$emit("update:show", false)
           }
       },
    }
</script>

<style scoped>

</style>