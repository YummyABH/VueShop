<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios'

import CardProduct from './CardProduct.vue';
import FilterProduct from './FilterProduct.vue';

const items = ref([]);
let totalProduct = ref();
let nameFilter = ref('Все товары')
let discount = [0, 1];
let remainderOfObjects;
let nameRequest = '*';

const limitNumber = 9;
let currentPage = 1;
onMounted(async () => {
    
    try {
        const { data } = await axios.get('https://cab54667e44c53ae.mokky.dev/items', {
            params: {
                page: currentPage,
                limit: limitNumber,
            }
        });
        items.value = data.items;
        remainderOfObjects = data.meta.remaining_count;
        totalProduct = data.meta.total_items;
        currentPage++
    } catch (err) {
        console.log(err);
    }
});

//--------Функция добавления товара по нажатию на кнопку

const loadMore = async() => {
    try {
        await axios.get(`https://cab54667e44c53ae.mokky.dev/items`, {
            params: {
                page: currentPage,
                limit: limitNumber,
                name: nameRequest,
                discount: discount,
            }
        })
            .then(response => {
                const newItem = response.data.items;
                items.value = [...items.value, ...newItem];
                remainderOfObjects = response.data.meta.remaining_count;
                currentPage++;
            })
            .catch(error => {
                console.error('Ошибка при выполнении запроса:', error);
            });
    } catch {}
}
//--------Функция фильрации по скидкеa
const dataDiscount = (text) => {
    nameFilter = text
    discount = 1
    axios.get('https://cab54667e44c53ae.mokky.dev/items', {
        params: {
            page: 1,
            limit: limitNumber,
            name: '*',
            discount: discount,
        }
    })
        .then(response => {
            const newItem = response.data.items;
            items.value = newItem;
            console.log(newItem);
            currentPage = 2;
            remainderOfObjects = response.data.meta.remaining_count
            totalProduct = response.data.meta.total_items;
        })
        .catch(error => {
            console.error('Ошибка при выполнении запроса:', error);
        });
}


//--------Функция фильрации по названию товара
const dataRequest = (text, allProducts) => {
    nameFilter = text
    discount = [0, 1];
    let res = '*' + text;
    if (allProducts) {
        res = '*'
    }

    axios.get('https://cab54667e44c53ae.mokky.dev/items', {
        params: {
            page: 1,
            limit: limitNumber,
            name: res,
            discount: discount
        }
    })
        .then(response => {
            nameRequest = res;
            const newItem = response.data.items;
            items.value = newItem;
            currentPage = 2;
            remainderOfObjects = response.data.meta.remaining_count
            totalProduct = response.data.meta.total_items;
        })
        .catch(error => {
            console.error('Ошибка при выполнении запроса:', error);
        });
}



</script>
    
<template>
    <div class="AllProducts">

        <header class="header">
            <h1 class="title" @click="">{{ nameFilter }}</h1>
            <div class="res">{{ totalProduct }} товара</div>
        </header>

        <div class="filter-button">
            <div class="filter-active">Фильтры</div>
            <div class="filter-icon">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <g clip-path="url(#clip0_3674_1165)">
                        <path d="M21 4V6H20L15 13.5V22H9V13.5L4 6H3V4H21ZM6.404 6L11 12.894V20H13V12.894L17.596 6H6.404Z"
                            fill="white" />
                    </g>
                    <defs>
                        <clipPath id="clip0_3674_1165">
                            <rect width="24" height="24" fill="white" />
                        </clipPath>
                    </defs>
                </svg>
            </div>
        </div>

        <div class="product">
            <FilterProduct @productRequest="dataRequest" @discountRequest="dataDiscount"></FilterProduct>
            <div class="product__wrapper">
                <div class="product__list">
                    <CardProduct v-for="item in items" :key="item.id" :data-card="item">
                        <img src="@assets/AllProducts/prodPreview.png" alt="">
                    </CardProduct>


                </div>
                <div class="product__add" v-if="remainderOfObjects" @click="loadMore">Показать ещё</div>
            </div>
        </div>
    </div>
</template>
  
  
<style scoped>
.AllProducts {
    width: 100%;
    margin: 60px 0px 40px 0px;
}

.header {
    margin: 40px 0px;
    align-items: end;
    display: flex;
    gap: 24px;
}

.title {
    font-size: 40px;
    font-style: normal;
    font-weight: 400;
    line-height: 48px;
}

.res {
    font-size: 16px;
    font-weight: 400;
    line-height: 125%;
    margin-bottom: 5px;
}

.product {
    gap: 40px;
    display: flex;
    justify-content: space-between;
}

.product__wrapper {
    align-items: center;
    flex: 1;
    display: flex;
    flex-direction: column;
}

.product__list {
    width: 100%;
    display: grid;
    grid-template: repeat(3, 1fr) / repeat(3, 1fr);
    row-gap: 15px;
    column-gap: 16px;
}

.product__add {
    margin-top: 40px;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
    align-items: center;

    border-radius: 8px;
    background-color: var(--back-hover);
    padding: 12px 20px;
    display: inline-block;

    &:hover {
        cursor: pointer;
        background-color: var(--dived-hover);
        transition-duration: 0.3s;
    }

    &:active {
        background-color: var(--back-hover);
    }
}



.filter-button {
    margin: 32px 0px;

    color: var(--text-light);
    display: none;
    width: 98px;
    gap: 4px;
    padding: 10px 14px 10px 20px;
    background-color: var(--back-button);
    border-radius: 8px;
}

.filter-active {
    display: flex;
    align-items: center;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: 20px;
}

.filter-icon {
    display: flex;
    align-items: center;
}

/*-----------------------------------MEDIA ЗАПРОСЫ---------*/

@media (max-width: 1280px) {
    .product__list {
        grid-template: repeat(4, 1fr) / repeat(2, 1fr);
    }

    .product__add {
        text-align: center;
        display: inline-block;
        width: 100%;
        padding-left: 0px;
        padding-right: 0px;
    }
}

@media (max-width: 1024px) {
    .filter-button {
        display: flex;
    }
}

@media (max-width: 768px) {
    .title {
        font-size: 24px;
        line-height: 28px;
    }

    .res {
        font-size: 14px;
        line-height: 16px;
    }

    .product__list {
        grid-template: repeat(6, 1fr) / repeat(1, 1fr);
    }
}
</style>
  