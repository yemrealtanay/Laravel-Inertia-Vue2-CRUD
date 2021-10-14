<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Profile
            </h2>
        </template>

        <div>
            <div class="max-w-7xl mx-auto py-10 sm:px-6 lg:px-8">

                <div class="overflow-hidden bg-white shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <form @submit.prevent="submit()">
                            <div>
                                <label for="name">Name</label>
                                <input type="text" id="name" v-model="form.name" class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600">
                            </div>
                            <div class="mt-4">
                                <label for="detail">Detail</label>
                                <textarea id="detail" type="text" v-model="form.detail" class="w-full px-4 py-2 mt-2 border rounded-md focus:outline-none focus:ring-1 focus:ring-blue-600"></textarea>
                            </div>

                            <div class="flex items-center mt-4">
                                <button type="submit" class="px-6 py-7 text-white bg-gray-900 rounded">Save</button>
                            </div>
                        </form>
                    </div>
                </div>

            </div>
        </div>
    </app-layout>
</template>


<script>

export default {
   data(){
     return{
         form: {
            name: null,
             detail: null,
         },
     }
   },
    methods:{
      submit(){
          this.$inertia.post(route("products.store", this.form));

      },
    },
};
</script>

