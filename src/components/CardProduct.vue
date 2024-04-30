<script setup>
import { ref } from 'vue'

const props = defineProps({
    dataCard: Object,
})

const translatedText = {
    name: 'Имя',
    capacity: 'Емкость',
    dimensions: 'Размеры',
    material: 'Материал',
    compatibility: 'Cовместимость',
};

function selectiveValue(value) {
    let textRes = ref('');
    for (const item in translatedText) {
        if (value == item) {
            textRes = translatedText[item];
            return textRes
        }
    }
}
</script>
    
<template>
    <div class="product__item">
        <router-link :to="{ path: '/ProductPage/', query: { productId: dataCard.id}}">
            <div class="container-img">
                <slot></slot>
            </div>
        </router-link>
        <div class="item__info">
            <div class="item__properties">

                <router-link :to="{ path: '/ProductPage/', query: { productId: dataCard.id}}">
                    <div class="item__title">{{ dataCard.name }}</div>
                </router-link>

                <div class="properties__data" v-for="(item, key) in dataCard.characteristics" :key="dataCard.index">
                    <div class="data-name">{{ selectiveValue(key) }}</div>
                    <div class="data-value">{{ item }}</div>
                </div>
            </div>

            <div class="item__price">
                <div class="price-item">{{ dataCard.price + " ₽" }}</div>
                <router-link :to="{ path: '/ProductPage/', query: { productId: dataCard.id}}">
                    <div class="price-button">Купить</div>
                </router-link>
            </div>
        </div>
    </div>
</template>

<style scoped>
.product__item {
    display: flex;
    flex-direction: column;
    border-radius: 16px;
    background-color: var(--back-hover);
    padding: 8px 8px 0px 8px;
}

.container-img {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    border-radius: 12px;

    background-color: #fff;
}

.item__info {
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: space-between;
    margin: 20px;
}

.item__properties {
    margin-bottom: 32px;
}

.item__title {
    margin-bottom: 8px;
    color: var(--text-dark);
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
}

.properties__data {
    padding: 8px 0px;
    border-bottom: 1px solid var(--dived-hover);
    display: flex;
    justify-content: space-between;
    gap: 8px;
}

.data-name {
    max-width: 40%;

    color: var(--text-hover);
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 16px;
}

.data-value {
    text-align: end;
    color: #000;
    font-size: 14px;
    font-style: normal;
    font-weight: 400;
    line-height: 16px;
}

.item__price {
    margin-top: 32px;
}

.price-item {
    color: var(--text-dark);

    font-size: 20px;
    font-style: normal;
    font-weight: 400;
    line-height: 24px;
    letter-spacing: -0.6px;
}

.price-button {
    text-align: center;
    padding: 12px 20px;
    border-radius: 8px;
    margin-top: 20px;

    background-color: var(--back-button);
    color: var(--text-light);
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
}
</style>