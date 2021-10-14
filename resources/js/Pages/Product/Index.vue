<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Profile
            </h2>
        </template>

        <div>
            <div class="max-w-7xl mx-auto py-10 sm:px-6 lg:px-8">

                <div class="p-6 bg-white border-b border-gray-200">
                    <div class="mb-4">
                        <a class="px-6 py-2 mb-2 text-green-100 bg-green-500 rounded" :href="route('products.create')">Create</a>
                    </div>
                    <table>
                        <thead class="font-bold bg-gray-300 border-b-2">
                        <td class="px-4 py-2">ID</td>
                        <td class="px-4 py-2">Name</td>
                        <td class="px-4 py-2">Detail</td>
                        <td class="px-4 py-2">Action</td>
                        </thead>
                        <tbody>
                        <tr v-for="product in products.data" :key="product.id">
                            <td class="px-4 py-2">{{ product.id }}</td>
                            <td class="px-4 py-2">{{ product.name }}</td>
                            <td class="px-4 py-2">{{ product.detail }}</td>
                            <td class="px-4 py-2 font-extrabold">
                                <a class="text-green-700" :href="route('products.edit', product.id)">Edit</a>
                                <button @click="destroy(product.id)" class="text-red-700">Delete</button>
                            </td>
                        </tr>
                        </tbody>
                    </table>
                </div>

            </div>
        </div>
    </app-layout>
</template>


<script>
    import AppLayout from '@/Layouts/AppLayout'

    export default {
        props:{
            products: Object,
        },
        methods:{
            destroy(id) {
                this.$inertia.delete(route("products.destroy", id));
            },
        }
    };
</script>

