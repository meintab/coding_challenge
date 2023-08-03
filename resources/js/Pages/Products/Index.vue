<script setup>
import BreezeAuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import {Head,Link,useForm} from "@inertiajs/vue3"
import BreezeButton from "@/Components/PrimaryButton.vue"
import {Inertia} from "@inertiajs/vue3" 

const props = defineProps({
    products: {
        type: Object,
        default: () => ({})
    }
});

const form = useForm();



</script>

<template>
    <Head title="Products" />
    <BreezeAuthenticatedLayout>
        <template #header>
            <h2 class="text-xl font-semibold text-gray-800">
                Products
            </h2>
        </template>
        <div class="py-12">
            <div class="mx-auto">
                <div 
                v-if="$page.props.flash.message"
                class="p-4 mb-4 text-sm text-green-700 rounded-lg"
                role="alert"
                >
                    <span class="font-medium">
                        {{ $page.props.flash.message }}
                    </span>
                </div>
                <div class="overflow-hiddin bg-white shadow-sm">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <div class="mb-2">
                            <Link :href="route('products.create')">
                                <BreezeButton>Add Blog</BreezeButton>
                            </Link>
                        </div>
                    </div>
                    <div>
                        <table>
                            <thead>
                                <tr>
                                    <th>Name</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr
                                v-for="product in products"
                                :key="product.id">
                                <td>{{product.name }}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

        </div>
    </BreezeAuthenticatedLayout>
</template>