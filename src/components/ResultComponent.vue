<template>
    <div>
        <DataView :value="products" :sortOrder="sortOrder" :sortField="sortField">
            <template #header>
                <Select v-model="sortKey" :options="sortOptions" optionLabel="label" placeholder="Sort By Price" @change="onSortChange($event)" />
            </template>
            <template #list="slotProps">
                <div class="flex flex-column">
                    <div v-for="(item, index) in slotProps.items" :key="index">
                        <div class="flex flex-column sm:flex-row sm:align-items-center p-6 gap-4" :class="{ 'border-top-1 surface-border': index !== 0 }">
                            <div class="md:w-10rem relative">
                                <img class="block mx-auto border-round w-full" :src="`https://primefaces.org/cdn/primevue/images/product/${item.image}`" :alt="item.name" />
                                <div class="absolute" style="left: 4px; top: 4px">
                                    <Tag :value="item.inventoryStatus" :severity="getSeverity(item)"></Tag>
                                </div>
                            </div>
                            <div class="flex flex-column md:flex-row justify-content-between md:align-items-center flex-1 gap-6">
                                <div class="flex flex-row md:flex-column justify-content-between align-items-start gap-2">
                                    <div>
                                        <span class="font-medium text-500 text-sm">{{ item.category }}</span>
                                        <div class="text-lg font-medium mt-2">{{ item.name }}</div>
                                    </div>
                                    <div class="surface-100 p-1" style="border-radius: 30px">
                                        <div class="surface-0 flex align-items-center gap-2 justify-content-center py-1 px-2" style="border-radius: 30px; box-shadow: 0px 1px 2px 0px rgba(0, 0, 0, 0.04), 0px 1px 2px 0px rgba(0, 0, 0, 0.06)">
                                            <span class="text-900 font-medium text-sm">{{ item.rating }}</span>
                                            <i class="pi pi-star-fill text-yellow-500"></i>
                                        </div>
                                    </div>
                                </div>
                                <div class="flex flex-column md:align-items-end gap-8">
                                    <span class="text-xl font-semibold">${{ item.price }}</span>
                                    <div class="flex flex-row-reverse md:flex-row gap-2">
                                        <Button icon="pi pi-heart" variant="outlined"></Button>
                                        <Button icon="pi pi-shopping-cart" label="Buy Now" :disabled="item.inventoryStatus === 'OUTOFSTOCK'" class="flex-auto md:flex-none white-space-nowrap"></Button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </template>
        </DataView>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { ProductService } from '@/service/ProductService'
import DataView from 'primevue/dataview'
import Select from 'primevue/select'
import Tag from 'primevue/tag'
import Button from 'primevue/button'

const products = ref()
const sortKey = ref()
const sortOrder = ref()
const sortField = ref()
const sortOptions = ref([
    { label: 'Price High to Low', value: '!price' },
    { label: 'Price Low to High', value: 'price' },
])

onMounted(() => {
    ProductService.getProductsSmall().then((data) => (products.value = data.slice(0, 5)))
})

const onSortChange = (event) => {
    const value = event.value.value
    const sortValue = event.value

    if (value.indexOf('!') === 0) {
        sortOrder.value = -1
        sortField.value = value.substring(1, value.length)
        sortKey.value = sortValue
    } else {
        sortOrder.value = 1
        sortField.value = value
        sortKey.value = sortValue
    }
}

const getSeverity = (product) => {
    switch (product.inventoryStatus) {
        case 'INSTOCK':
            return 'success'
        case 'LOWSTOCK':
            return 'warn'
        case 'OUTOFSTOCK':
            return 'danger'
        default:
            return null
    }
}
</script>
