<script setup>
import ItemOrder from './ItemOrder.vue'
import { onMounted, watchEffect, ref } from 'vue';
import axios from 'axios'

const items = ref([])
let dataQuantity = []

const deleteProduct = async (idItem) => {
    try {
        await axios.delete(`https://de28c738d58495a7.mokky.dev/items/${idItem}`)
        .then(
            items.value = items.value.filter(item => item.id !== idItem)
        )
    } catch (err) {
        console.log(err);
    }
}
onMounted(async () => {
    try {
        const { data } = await axios.get('https://de28c738d58495a7.mokky.dev/items');
        items.value = data;
        dataQuantity = [
            items.value.map((item) => {
                return item.quantity;
            })
        ]
    } catch (err) {
        console.log(err);
    }
});
const sum = ref(0);
function updateQuantity(value, id) {
    console.log(value);
    if (value > 0) {
        dataQuantity[0][id - 1] = value
        sum.value = 0
    } 
}

watchEffect(() => {
    for (let index = 0; index < items.value.length; index++) {
        if (items.value.length > 0) {
            sum.value += items.value[index].price * dataQuantity[0][index];
        }
    }
});
</script>

<template>
    <div class="subtitle">
        Мой заказ
    </div>
    <div class="container">
        <ItemOrder v-for="item in items" :key="item.id" :data-card="item" @arr-data-quantity="updateQuantity" @delete-product="deleteProduct" />
    </div>
    <div class="check-container">
        <div class="pay">К оплате:</div>
        <div class="res">{{ sum }} ₽</div>
    </div>
</template>


<style scoped>
.subtitle {
    margin-bottom: 32px;

    font-size: 24px;
    font-weight: 400;
    line-height: 28px;

    color: var(--text-dark);
}

.check-container {
    gap: 16px;
    padding-top: 16px;
    border-top: 1px solid var(--dived-hover);
    width: 100%;
    display: flex;
    justify-content: space-between;
}

.pay {
    font-size: 20px;
    font-weight: 400;
    line-height: 28px;
}

.res {
    font-size: 16px;
    font-weight: 400;
    line-height: 20px;
}

/*-----------------------------Media---------------------*/

@media (max-width: 1280px) {}

@media (max-width: 1024px) {}

@media (max-width: 768px) {
    .pay {
        min-width: 66px;
        font-size: 14px;
        line-height: 16px;
    }

    .res {
        font-size: 14px;
        line-height: 16px;
    }
}
</style>
